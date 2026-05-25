# Saarthi Railway Companion

Saarthi Railway Companion is a full-stack railway station assistant built to help passengers navigate stations, check train schedules, request assistance, and access real-time service updates in one place.

It combines a React + Vite frontend, an Express + MongoDB backend, Socket.IO for live updates, and an AI-powered chat assistant with a fallback response system when the AI provider is unavailable.

## What It Does

- Interactive station navigation with map-based guidance
- Live train and platform updates through Socket.IO
- AI assistant for station and travel questions
- User authentication and profile management
- Booking flows for cloakroom, coolie, and wheelchair services
- Assistance request form for accessibility and emergency support
- Admin dashboard for posting operational updates
- Accessibility-friendly UI with dark mode, voice support, and translation helpers

## Tech Stack

- Frontend: React, Vite, Tailwind CSS, Framer Motion
- Maps/UI: Leaflet, React Leaflet, React Icons, Lucide React
- Realtime: Socket.IO
- Backend: Node.js, Express, MongoDB, Mongoose
- Auth: JWT, bcryptjs
- AI: Groq SDK, OpenAI SDK dependency present

## Project Structure

```text
client/   # React frontend
server/   # Express API, MongoDB models, and Socket.IO handlers
```

## Prerequisites

- Node.js 18+ recommended
- npm
- MongoDB running locally or a MongoDB Atlas connection string

## Setup

### 1. Install dependencies

Install the frontend and backend dependencies separately:

```bash
cd server
npm install

cd ../client
npm install
```

### 2. Configure environment variables

Create a `.env` file in `server/`:

```env
PORT=5000
CLIENT_URL=http://localhost:3000
MONGODB_URI=mongodb://localhost:27017/saarthi
JWT_SECRET=your_super_secret_key
GROQ_API_KEY=your_groq_api_key_optional
```

Create a `.env` file in `client/`:

```env
VITE_API_URL=http://localhost:5000
```

Note: the Vite dev server proxy is configured to forward API and Socket.IO requests to `http://localhost:5000`, so using port `5000` for the backend keeps local development aligned.

### 3. Start the backend

```bash
cd server
npm run dev
```

The API will be available at `http://localhost:5000/api`.

### 4. Start the frontend

```bash
cd client
npm run dev
```

The app will run at `http://localhost:3000`.

## Available Scripts

### Client

From `client/`:

- `npm run dev` - start the Vite development server
- `npm run build` - build the frontend for production
- `npm run lint` - run ESLint
- `npm run preview` - preview the production build locally

### Server

From `server/`:

- `npm run dev` - start the API with nodemon
- `npm start` - start the API with Node.js

## Main Features

### Home

- Landing page with live status summaries
- Feature highlights and quick access to the core tools

### Station Map

- Route planning between station points
- Accessibility mode with alternate routing
- Visual station markers and navigation steps

### Train Schedule

- Search trains by route
- Filter by train type
- View train timelines and details

### Booking

- Cloakroom booking
- Coolie booking
- Wheelchair booking

### Assistance

- Submit support requests for medical, security, mobility, or lost-property help

### Dashboard

- Personalized user dashboard
- Quick actions for navigation, assistance, booking, and train tracking

### Admin

- Manage trains and announcements
- Push live updates to connected clients

## Backend Notes

- On startup, the server seeds sample train and station records if the database is empty.
- The chat route falls back to helpful mock responses when the Groq API key is not configured.
- Authentication uses JWT and protected routes require a valid bearer token.

## Troubleshooting

- If the frontend cannot reach the API, confirm that `VITE_API_URL` matches the backend port.
- If real-time updates are not showing, check that Socket.IO is running on the same backend URL as the API.
- If MongoDB is disconnected, the server will log the connection error on startup.

## License

MIT
