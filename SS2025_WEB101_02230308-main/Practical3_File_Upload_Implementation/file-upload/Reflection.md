# Practical 3: File Upload Implementation Reflection

## Documentation 

### Main Concepts Applied

1. Multipart Form Data Handling
- Used FormData on the client and formidable on the server to handle file uploads.

- Disabled Next.js default body parser to allow raw multipart data.

- export const config = { api: { bodyParser: false } };

2. File Validation (Client & Server)
- Checked file type (.jpg, .png, .pdf, etc.) and size (max 5MB).

- Ensured validation rules were consistent across frontend and backend.

3. Upload Progress Tracking
- Used Axios onUploadProgress to show real-time progress bar.

- Improved feedback by displaying messages like “Processing...” after 100%.

4. Drag and Drop UI
- Implemented with react-dropzone.

- Included visual feedback and support for multiple file uploads.

5. Form State Management
- Managed with react-hook-form and local state.

- Displayed inline error messages and disabled upload button 
during active uploads.

## Challenges & How I Solved Them
### Next.js Body Parser Conflict
- Issue: Default body parser interfered with file uploads.
- Fix: Disabled it using api: { bodyParser: false }.

### Client-Server Validation Mismatch
- Issue: Different rules caused confusion.
- Fix: Centralized validation rules in a shared constant.

### Inaccurate Progress Bar
- Issue: Showed 100% before upload was really done.
- Fix: Waited for server response to confirm completion.

### Confusing Error Messages
- Issue: Users didn’t know what went wrong.
- Fix: Showed specific messages for file size/type/network errors.

### Drag UI State Glitches
- Issue: Drag state got stuck.
- Fix: Reset drag state properly on all drag events.

## Key Takeaways
- Good UX matters: Even small UI details like progress bars or file previews improve the experience.

- Security is critical: Never rely only on client-side checks.

- Error clarity helps users: Descriptive error messages prevent frustration.

- Keep things consistent: Sync validation and logic across the stack.

## Future Improvement
- Add image/file previews before upload

- Use chunked uploads for larger files

- Store files in cloud (like S3)

- Add virus scanning for security

- Improve test coverage for edge cases