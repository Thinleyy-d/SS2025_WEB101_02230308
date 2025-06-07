
# Practical 5: Implementing Infinite Scroll Reflection 

## Documentation 

### Main Concepts Applied

In this practical, I implemented **infinite scrolling** for a TikTok-style video feed using **TanStack Query** (`useInfiniteQuery`) and **cursor-based pagination**. This approach provides a smoother and more efficient user experience compared to traditional pagination.

---

## What I Learned

- The difference between **cursor-based** and **offset-based** pagination
- How to use `useInfiniteQuery` from TanStack Query to load more content dynamically
- Leveraging the **Intersection Observer API** to detect when the user scrolls near the bottom
- Structuring backend and frontend to work together efficiently for paginated data fetching

---

## Key Technologies

| Tool / Concept            | Use Case                                 |
|---------------------------|------------------------------------------|
| Prisma                    | Fetch paginated video data from DB       |
| TanStack Query            | Handle infinite queries & caching        |
| Intersection Observer API | Detect scrolling into view               |
| Next.js + React           | Frontend UI and page layout              |

---

## Backend Highlights

- Introduced `cursor` & `limit` query params
- Used Prisma's `.findMany()` with cursor-based pagination
- Returned `nextCursor` and `hasNextPage` in API response
- Applied same logic for both general and "Following" video feeds

---

## Frontend Highlights

- Set up `QueryClientProvider` in the app root
- Built custom `useIntersectionObserver` hook
- Used `useInfiniteQuery` to manage pagination state
- Dynamically loaded more videos as user scrolls

---

## Testing Scenarios

- Videos load on initial page render
- More videos load on scroll
- Loader and "end reached" messages appear correctly
- Works under slow network conditions
- Error state shown when API fails

---

## Key Takeaways

- Cursor-based pagination is more reliable for dynamic content
- TanStack Query handles infinite scroll elegantly
- Clean UI requires careful loading state handling
- Observer-based triggers are more performant than scroll listeners

---

## Next Steps

- Add video virtualization for performance on long feeds
- Show retry button on error
- Implement infinite scroll on other pages (e.g., following tab)


---

**Reflection**: This practical helped me understand how to handle paginated data efficiently. Building infinite scroll from scratch gave me hands-on experience with both frontend UX and backend data control. Overall, it significantly improved the user flow and performance of the video feed.