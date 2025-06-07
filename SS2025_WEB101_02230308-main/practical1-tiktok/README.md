# TikTok Clone with Next.js

A simplified TikTok web interface built using Next.js, React, and Tailwind CSS.

### Main Features
- TikTok-like layout with sidebar
- Scrollable video feed
- Pages: Home, Profile, Upload, Explore, Live
- Login & signup forms with validation
- Works on mobile and desktop

### Built With
- Next.js (App Router)
- React
- Tailwind CSS
- React Hook Form (for forms)
- React Icons

## Quick Start

### Step 1: Clone the repo

git clone https://github.com/02230308/SS2025_WEB101_02230308.git

cd practical1-tiktok

### Step 2: Create Next.js Project

npx create-next-app@latest


Configure with these settings:
- TypeScript: No (using JSX)
- ESLint: Yes
- Tailwind CSS: Yes
- src/ directory: Yes
- App Router: Yes
- Default import alias: No

### Step 3: Install Dependencies

npm install react-icons react-hook-form


### Step 4: Start Development Server

npm run dev


Visit `http://localhost:3000` to view the application.

## Project Structure

```
src/
├── app/
│   ├── layout.js          # Root layout
│   ├── page.js            # Home page 
│   ├── globals.css        # Global styles
│   ├── profile/
│   │   └── page.jsx       # Profile page
│   ├── upload/
│   │   └── page.jsx       # Upload page
│   ├── login/
│   │   └── page.jsx       # Login page
│   ├── signup/
│   │   └── page.jsx       # Registration page
│   ├── following/
│   │   └── page.jsx       # Following page feed
│   ├── explore/
│   │   └── page.jsx       # Explore page
│   └── live/
│       └── page.jsx       # Live page
├── components/
│   ├── layout/
│   │   └── MainLayout.jsx # Main layout component
│   └── ui/
│       ├── VideoCard.jsx  # Individual video component
│       └── VideoFeed.jsx  # Video feed container
└── lib/                   # Utility functions
```

## Key Components

Main Layout - Sidebar + header

Video Cards - Shows videos with like/comment buttons

Forms - Login & signup with error checking

## Testing Tips
### Try forms with:

- Empty fields

- Wrong email formats

- Short passwords

- Check all menu links work

- Try on different screen sizes

## Future Improvements
- Add real user accounts

- Enable video uploads

- Connect to database

- Add comments feature

## Learning Points
- Building reusable components

- Form validation

- Responsive design

- Next.js routing

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [React Documentation](https://legacy.reactjs.org/docs)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [React Hook Form](https://react-hook-form.com/)
- [React Icons](https://react-icons.github.io/react-icons/)



