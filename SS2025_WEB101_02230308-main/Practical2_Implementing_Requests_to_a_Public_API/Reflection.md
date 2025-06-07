# Practical 2: Implementing Requests to a Public API ( RESTful API Weather Application ) Reflection 

## Key Concepts Applied

### 1. RESTful API Methods
- **GET**: Fetched real-time weather using OpenWeatherMap.
- **POST**: Sent new location data to JSONPlaceholder.
- **PUT**: Updated existing records by ID.
- **DELETE**: Removed records with confirmation and status checks.

### 2. Asynchronous JavaScript
- Used `async/await` for clean async flow.
- Handled promises and errors effectively.
- Made HTTP calls using the modern Fetch API.

### 3. Error Handling & UX
- Displayed loading, success, and error states.
- Validated inputs before API calls.
- Ensured app stayed functional even if APIs failed.

### 4. Data Management
- Used `localStorage` to persist data.
- Synced UI with real-time updates.
- Formatted requests using JSON.

### 5. Modern Web Practices
- Responsive layout using CSS Flexbox/Grid.
- Semantic HTML for accessibility.
- Separated HTML, CSS, and JS clearly.

---

## What I Learned

### Technical
- Integrated multiple APIs with authentication.
- Understood REST principles and HTTP methods.
- Gained confidence in writing clean, modular ES6+ JavaScript.
- Designed user-friendly and responsive interfaces.

### Conceptual
- Appreciated good API design and documentation.
- Learned to manage app state and data flow.
- Understood client-server separation.

---

## Challenges & Solutions

- **CORS Issues**: Resolved by choosing CORS-compliant APIs and learning about browser restrictions.
- **API Key Exposure**: Documented placeholder usage and learned about secure key handling with environment variables.
- **Error Inconsistency**: Built a unified error system to handle different formats gracefully.
- **UI Sync**: Ensured data and interface stayed in sync using simple state logic.
- **Responsive Design**: Designed layouts mobile-first using media queries and flexible grids.

---

## Key Takeaways

- **Good UX** > Just Working Code.
- **Secure Practices**: Never expose sensitive info.
- **Testing Matters**: Handled edge cases and failures early.
- **API Design** impacts ease of development.

---

## Future Enhancements

- Add a backend to protect keys and handle requests.
- Replace `localStorage` with a real database.
- Add login, saved locations, and weather history.
- Automate testing for better reliability.

---

## Conclusion

This project helped solidify my understanding of RESTful APIs, async JavaScript, and user-centered design. It was a great step toward building 
modern, secure, and scalable web apps.

