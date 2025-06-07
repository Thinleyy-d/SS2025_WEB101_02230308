# Practical 3: File Upload Implementation

A modern React/Next.js app for uploading files with drag-and-drop, validation, progress tracking, and responsive design.

## Features

- Upload multiple files (max 10)
- Drag & drop support (via `react-dropzone`)
- File type & size validation (max 5MB)
- Real-time upload progress
- Friendly error messages
- Responsive UI (styled with Tailwind CSS)

## Tech Stack

- **Next.js** – App framework with API routes
- **React Hook Form** – Form state & validation
- **Axios** – HTTP requests + progress tracking
- **Formidable** – Handles file uploads server-side
- **React Dropzone** – Drag-and-drop support
- **Tailwind CSS** – Utility-first styling

---

## Project Structure

```
file-upload/
├── pages/
│ ├── index.js # Upload UI
│ └── api/upload.js # Upload API handler
├── uploads/ # Uploaded files
├── next.config.js
└── README.md
```

---

## How to Run

### 1. Create the Project

```bash
npx create-next-app file-upload
cd file-upload

```
### 2. Install Dependencies

- npm install react-hook-form react-dropzone axios formidable

### 3. Add Tailwind CSS

- npm install -D tailwindcss postcss autoprefixer
- npx tailwindcss init -p

- Update configs and import Tailwind in styles/globals.css:
   - @tailwind base;
   - @tailwind components;
   - @tailwind utilities;

### 4. Start the Dev Server

- npm run dev
- Visit http://localhost:3000

## File Upload Rules
- Types: JPG, PNG, GIF, PDF, TXT

- Size: Max 5MB per file

- Max Files: 10 per upload

- Progress: Shows % complete and status

- Errors: Clear feedback for invalid files

## Backend (API)
- Uses formidable to parse multipart data

- Auto-creates the /uploads folder

- Generates unique file names

- Validates size/type server-side

- Sends back status responses

## Security Highlights
- Validates file types on both ends

- Rejects oversized files

- Prevents overwriting with unique names

- Isolates uploads from public access

## Config Options
### In pages/api/upload.js:
- const form = formidable({
  maxFileSize: 5 * 1024 * 1024,
  maxFiles: 10,
  // more options...
});

### Allowed types:
- const allowedTypes = ['image/jpeg', 'image/png', 'image/gif', 'application/pdf', 'text/plain'];


## Troubleshooting
- Module errors? Run npm install

- Upload issues? Check folder permissions

- File rejections? Ensure valid types and sizes

- API errors? Add logs and debug in upload.js

## Future Ideas
- Preview images before upload

- Support file compression

- Add login and file metadata

- Integrate with S3 or Firebase

- Resume broken uploads




