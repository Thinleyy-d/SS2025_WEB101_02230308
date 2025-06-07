## NOTE: The actual practical work implementation is done in practical1-tiktok folder. This folder is just for README.md and Reflection.md.

# Practical 5: Implementing Infinite Scroll 

## Overview
In this practical, I implemented infinite scrolling in the TikTok app using **TanStack Query** with **cursor-based pagination**. The goal was to load videos seamlessly as users scroll, ensuring performance and a better UX.

## Core Concepts

### Cursor vs Offset Pagination
- **Offset-based**: Prone to issues with dynamic data; uses page numbers.
- **Cursor-based**: More stable; uses a reference ID to fetch the next batch. Ideal for infinite scroll.

### TanStack Query Advantages
- `useInfiniteQuery` handles pagination automatically
- Smart caching, background updates, and error handling
- Great for scalable data fetching in React apps

### Intersection Observer
- Efficiently detects when an element (like a “load more” trigger) enters the viewport
- Better than listening to scroll events

---
## Implementation Steps

### Part 1: Backend Implementation

#### Step 1: Update Video Controller
```javascript
// src/controllers/videoController.js
const getAllVideos = async (req, res) => {
  const { cursor, limit = 10 } = req.query;
  const limitNum = parseInt(limit);
  
  try {
    const videos = await prisma.video.findMany({
      take: limitNum + 1, // n+1 pattern
      cursor: cursor ? { id: cursor } : undefined,
      skip: cursor ? 1 : 0,
      orderBy: { createdAt: 'desc' },
      include: {
        user: true,
        likes: true,
        comments: true
      }
    });
    
    const hasNextPage = videos.length > limitNum;
    const videosToReturn = hasNextPage ? videos.slice(0, -1) : videos;
    const nextCursor = hasNextPage ? videos[videos.length - 1].id : null;
    
    res.json({
      videos: videosToReturn,
      nextCursor,
      hasNextPage
    });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};
```

#### Step 2: Update Following Videos Controller

```javascript
const getFollowingVideos = async (req, res) => {
  const { cursor, limit = 10 } = req.query;
  const userId = req.user.id;
  const limitNum = parseInt(limit);
  
  try {
    const videos = await prisma.video.findMany({
      take: limitNum + 1,
      cursor: cursor ? { id: cursor } : undefined,
      skip: cursor ? 1 : 0,
      where: {
        user: {
          followers: {
            some: { followerId: userId }
          }
        }
      },
      orderBy: { createdAt: 'desc' },
      include: {
        user: true,
        likes: true,
        comments: true
      }
    });
    
    const hasNextPage = videos.length > limitNum;
    const videosToReturn = hasNextPage ? videos.slice(0, -1) : videos;
    const nextCursor = hasNextPage ? videos[videos.length - 1].id : null;
    
    res.json({
      videos: videosToReturn,
      nextCursor,
      hasNextPage
    });
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
};
```

### Part 2: Frontend Implementation

#### Step 1: Install Dependencies
- npm install @tanstack/react-query @tanstack/react-query-devtools


#### Step 2: Set Up Query Client Provider

```javascript
// src/app/layout.js
'use client';
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import { ReactQueryDevtools } from '@tanstack/react-query-devtools';
import { useState } from 'react';

export default function RootLayout({ children }) {
  const [queryClient] = useState(() => new QueryClient({
    defaultOptions: {
      queries: {
        staleTime: 60 * 1000, // 1 minute
        cacheTime: 5 * 60 * 1000, // 5 minutes
      },
    },
  }));

  return (
    <html lang="en">
      <body>
        <QueryClientProvider client={queryClient}>
          {children}
          <ReactQueryDevtools initialIsOpen={false} />
        </QueryClientProvider>
      </body>
    </html>
  );
}
```

#### Step 3: Update Video Service

```javascript
// src/services/videoService.js
const API_BASE_URL = process.env.NEXT_PUBLIC_API_URL || 'http://localhost:5000';

export const fetchVideos = async ({ pageParam = null }) => {
  const url = new URL(`${API_BASE_URL}/api/videos`);
  if (pageParam) {
    url.searchParams.append('cursor', pageParam);
  }
  url.searchParams.append('limit', '10');
  
  const response = await fetch(url);
  if (!response.ok) {
    throw new Error('Failed to fetch videos');
  }
  
  return response.json();
};

export const fetchFollowingVideos = async ({ pageParam = null }) => {
  const url = new URL(`${API_BASE_URL}/api/videos/following`);
  if (pageParam) {
    url.searchParams.append('cursor', pageParam);
  }
  url.searchParams.append('limit', '10');
  
  const token = localStorage.getItem('token');
  const response = await fetch(url, {
    headers: {
      'Authorization': `Bearer ${token}`
    }
  });
  
  if (!response.ok) {
    throw new Error('Failed to fetch following videos');
  }
  
  return response.json();
};
```

#### Step 4: Create Intersection Observer Hook

```javascript
// src/hooks/useIntersectionObserver.js
import { useEffect, useRef } from 'react';

export const useIntersectionObserver = (callback, options = {}) => {
  const targetRef = useRef(null);

  useEffect(() => {
    const target = targetRef.current;
    if (!target) return;

    const observer = new IntersectionObserver(([entry]) => {
      if (entry.isIntersecting) {
        callback();
      }
    }, {
      threshold: 0.1,
      rootMargin: '100px',
      ...options
    });

    observer.observe(target);

    return () => {
      if (target) {
        observer.unobserve(target);
      }
    };
  }, [callback, options]);

  return targetRef;
};
```

#### Step 5: Update VideoFeed Component

```javascript
// src/components/ui/VideoFeed.jsx
'use client';
import { useInfiniteQuery } from '@tanstack/react-query';
import { useIntersectionObserver } from '@/hooks/useIntersectionObserver';
import { fetchVideos } from '@/services/videoService';
import VideoCard from './VideoCard';

export default function VideoFeed() {
  const {
    data,
    fetchNextPage,
    hasNextPage,
    isFetchingNextPage,
    isLoading,
    isError,
    error
  } = useInfiniteQuery({
    queryKey: ['videos'],
    queryFn: fetchVideos,
    getNextPageParam: (lastPage) => lastPage.nextCursor,
    staleTime: 5 * 60 * 1000, // 5 minutes
  });

  const loadMoreRef = useIntersectionObserver(() => {
    if (hasNextPage && !isFetchingNextPage) {
      fetchNextPage();
    }
  });

  if (isLoading) {
    return (
      <div className="flex justify-center items-center h-64">
        <div className="animate-spin rounded-full h-8 w-8 border-b-2 border-pink-500"></div>
      </div>
    );
  }

  if (isError) {
    return (
      <div className="text-center text-red-500 p-4">
        Error: {error.message}
      </div>
    );
  }

  const videos = data?.pages.flatMap(page => page.videos) || [];

  return (
    <div className="space-y-4">
      {videos.map((video) => (
        <VideoCard key={video.id} video={video} />
      ))}
      
      {/* Loading trigger element */}
      <div ref={loadMoreRef} className="h-10 flex justify-center items-center">
        {isFetchingNextPage && (
          <div className="animate-spin rounded-full h-6 w-6 border-b-2 border-pink-500"></div>
        )}
        {!hasNextPage && videos.length > 0 && (
          <p className="text-gray-500">🎉 You've reached the end!</p>
        )}
      </div>
    </div>
  );
}
```
## Implementation Summary

### Backend (Express + Prisma)
- Used Prisma's `cursor`, `skip`, and `take` for fetching
- Returned `nextCursor` and `hasNextPage` to the frontend

```js
// Simplified structure
const videos = await prisma.video.findMany({
  take: limit + 1,
  cursor: cursor ? { id: cursor } : undefined,
  skip: cursor ? 1 : 0,
});
```

### Frontend (Next.js + React Query)
- Installed @tanstack/react-query and devtools

- Wrapped app with QueryClientProvider

- Created useInfiniteQuery hooks to fetch videos

- Used a custom useIntersectionObserver hook to trigger fetchNextPage()

- Displayed loading spinners and end-of-list message

## Resources 

- [TanStack Query Documentation](https://tanstack.com/query/latest)
- [useInfiniteQuery Guide](https://tanstack.com/query/latest/docs/react/guides/infinite-queries)
- [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)
- [Prisma Cursor-Based Pagination](https://www.prisma.io/docs/concepts/components/prisma-client/pagination)
- [Next.js App Router Documentation](https://nextjs.org/docs/app)


## Testing Done

- Videos load in batches as you scroll

- “Load more” triggers correctly

- Handles slow networks with loading states

- Avoids duplicate video loads

- Graceful error display on fetch failure


## Performance Tips

- Use React Query’s caching to reduce redundant requests

- Virtualize video lists for long feeds

- Debounce or throttle fetch calls when needed

- Clean up observers properly to avoid memory leaks

