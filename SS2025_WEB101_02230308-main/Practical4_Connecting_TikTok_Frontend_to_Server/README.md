## NOTE: The actual practical work implementation is done in practical1-tiktok folder. This folder is just for README.md and Reflection.md.

# Practical 4: Connecting TikTok Frontend to Server

## Overview
This practical connects a TikTok-like Next.js frontend with an Express.js backend, featuring user authentication, video display, and social interactions.

## Setup & Installation
### Prerequisites
- Node.js installed

- Backend server running (Express)

- Frontend project (Next.js)

### Install Dependencies
- npm install axios jwt-decode react-hot-toast


### Environment Variable
#### .env.local
- NEXT_PUBLIC_API_URL=http://localhost:8000/api

## Key Features
### Authentication
- JWT-based login/logout

- Protected routes

- Persistent login state

### Video System
- Upload videos with caption & thumbnail

- Like, comment, and playback support

- Personalized "Following" and "For You" feeds

### Social Features
- Follow/unfollow users

- Explore user profiles

- User discovery and search

### API Integration
- Centralized Axios API client

- Error handling + loading states

- Auth token attached via interceptor

## Folder Structure
```
src/
├── app/               → pages like profile, upload, explore
├── components/        → UI, layout, auth components
├── contexts/          → Auth context provider
├── lib/               → API config setup
└── services/          → Video & user API services
```


## Testing Checklist
### Auth Flow
- Register & login multiple users

- Verify login state across pages

### Video Interactions
- Upload videos, test playback

- Like/comment functionality

### Navigation & UI
- Protected route access

- Authentication-based UI display

## Troubleshooting Tips
### Issue:	
1. CORS errors	
2. Login fails	
3. API errors	
4. Upload issues	

### Fix:
1. Ensure backend allows frontend origin
2. Check token format/expiry
3. Confirm backend server and API URL
4. Verify file type/size and server-side validation