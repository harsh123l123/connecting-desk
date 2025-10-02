# Copilot Instructions for Fullstack Chat App

## Project Overview
- **Monorepo** with `backend` (Node.js/Express) and `frontend` (React/Vite)
- **Backend**: REST API, JWT auth, Socket.io for real-time chat, MongoDB, email (Resend), image uploads (Cloudinary), rate-limiting (Arcjet)
- **Frontend**: React, Zustand for state, Tailwind CSS, DaisyUI, Vite

## Key Workflows
- **Backend**: Start with `npm run dev` in `/backend` (uses nodemon)
- **Frontend**: Start with `npm run dev` in `/frontend` (Vite dev server)
- **Environment**: See `.env` example in root README for required secrets
- **MongoDB**: Local or cloud connection via `MONGO_URI`

## Architecture & Patterns
- **Auth**: Custom JWT, see `/backend/src/controllers/auth.controller.js` and `/backend/src/middleware/auth.middleware.js`
- **Real-time**: Socket.io setup in `/backend/src/lib/socket.js`, used for chat and presence
- **Emails**: Handled in `/backend/src/emails/` via Resend API
- **Image Uploads**: `/backend/src/lib/cloudinary.js` for Cloudinary integration
- **Rate Limiting**: Arcjet middleware in `/backend/src/middleware/arcjet.middleware.js`
- **Models**: Mongoose schemas in `/backend/src/models/`
- **Frontend State**: Zustand stores in `/frontend/src/store/`
- **UI**: Components in `/frontend/src/components/`, styled with Tailwind/DaisyUI

## Conventions & Tips
- **No 3rd-party auth**: All authentication is custom JWT
- **API endpoints**: Defined in `/backend/src/routes/`
- **Frontend API calls**: Use `/frontend/src/lib/axios.js` for HTTP requests
- **Sounds**: UI sound effects in `/frontend/public/sounds/`, toggled via Zustand
- **Testing**: No formal test suite detected; manual testing via dev servers
- **Deployment**: Designed for free-tier hosting (e.g., Sevalla)

## Integration Points
- **Socket.io**: Both backend and frontend communicate for chat, presence, notifications
- **Resend**: Used for transactional emails (signup, etc.)
- **Cloudinary**: Used for image uploads from frontend to backend
- **Arcjet**: API rate-limiting middleware

## Example: Adding a New API Route
1. Create controller in `/backend/src/controllers/`
2. Add route in `/backend/src/routes/`
3. Update model in `/backend/src/models/` if needed
4. Use `/frontend/src/lib/axios.js` to call new endpoint

## References
- See root `README.MD` for setup and environment details
- See `/backend/src/server.js` for backend entrypoint
- See `/frontend/src/main.jsx` for frontend entrypoint

---
_Iterate and update this file as new patterns or workflows emerge._
