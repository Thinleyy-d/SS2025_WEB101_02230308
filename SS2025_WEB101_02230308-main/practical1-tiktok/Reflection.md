# Practical 1: Tiktok Clone Reflection

## Documentation 

### Concepts Applied

1. Next.js Routing

- Used the App Router (/app) for seamless navigation between pages.

- Implemented dynamic layouts (e.g., sidebar persists across routes).

2. Tailwind CSS

- Styled components directly in JSX for faster development.

- Used utility classes for responsive design (e.g., flex, grid).

3. Form Handling

- Integrated react-hook-form for efficient form validation.

- Added real-time error feedback (e.g., password strength, email format).

4. State Management

- Managed UI states (e.g., loading spinners, like buttons) with useState.

### What I Learned

- Next.js Optimization: Leveraged server-side rendering for better performance.

- Component Reusability: Broke down UI into smaller components (e.g., VideoCard).

- Form Best Practices: Learned to validate inputs before submission to reduce errors.

### Challenges & Solutions


1. Challenge: Sidebar layout broke on smaller screens.
- Solution: Used Tailwind’s responsive classes (md:flex, hidden).

2. Challenge: Form validation logic was complex.
- Solution: Used react-hook-form’s built-in validators (e.g., required, pattern).

3. Challenge: Mock data organization.
- Solution: Created a DUMMY_POSTS array to simulate API responses.



### Future Improvements

- Add Firebase/auth for real user authentication.

- Implement video upload functionality.

- Optimize performance with lazy loading.
