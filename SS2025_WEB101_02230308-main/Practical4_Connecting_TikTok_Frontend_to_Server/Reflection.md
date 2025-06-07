# Practical 4: Connecting TikTok Frontend to Server Reflection

## Key Concepts Covered

### 1. Full-Stack Integration
Connected a **Next.js** frontend to an **Express.js** backend to build a functional social video app.

### 2. Authentication System
- JWT-based login/logout
- Auth state handled with React Context
- Tokens stored securely and attached to requests
- Protected routes for logged-in users only

### 3. API & State Architecture
- Centralized **Axios client** with interceptors
- Separated logic into **service layers**
- Managed loading, success, and error states

### 4. Component Design
- Reusable components (Modal, Forms, VideoCard)
- Clean separation between UI, logic, and data
- Controlled prop/state flow across components

### 5. Social Features
- Video feed with "For You" and "Following"
- Like, comment, and follow interactions
- Real-time UI updates on user actions

---

## What I Learned

### Technical Skills
- Consuming REST APIs and handling JWT auth
- Managing global state using React Context
- Structuring services for scalability
- Handling file uploads and form validations

### Conceptual Growth
- Clear understanding of **client-server communication**
- Applied separation of concerns in architecture
- Designed **responsive** and **user-friendly** UIs
- Improved security awareness with token-based auth

---

## Challenges & Solutions

| Challenge                         | Solution                                                              |
|-----------------------------------|-----------------------------------------------------------------------|
| CORS Errors                       | Configured proper CORS headers in backend                             |
| Auth state lost on refresh        | Used `localStorage` and initialized context on app load               |
| Inconsistent error messages       | Set up global Axios error interceptor + toast notifications           |
| Complex state between comps       | Used Context + custom hooks to simplify data flow                     |
| Video uploads failing             | Added file validation, progress bar, and optimized upload settings    |

---

## Key Takeaways

- A clean architecture = easier debugging & faster development  
- Feedback & loading states enhance user trust  
- Auth and error handling need to be baked into every feature  
- Real-world testing (with multiple accounts) is critical  
- Good documentation saves time and helps others understand your code

---

## Looking Ahead

- Add video lazy loading & caching for better performance  
- Improve token security with refresh tokens  
- Add unit and integration tests  
- Introduce real-time notifications  

---

## Final Thoughts

This practical helped me understand how to **build full-stack apps from scratch**, combining frontend UI with backend logic. I got hands-on 
experience with **authentication, API integration, file handling**, and designing social media-style features. The knowledge gained here is a 
solid foundation for future professional-grade web applications.
