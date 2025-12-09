# How to Run the Application

This guide will help you run both the backend and frontend of the Clean Street App.

## Prerequisites

- **Node.js** (v16 or higher) - [Download Node.js](https://nodejs.org/)
- **MongoDB** - Either:
  - Local MongoDB installation, OR
  - MongoDB Atlas account (free tier available)
- **npm** (comes with Node.js)

## Step 1: Install Dependencies

### Backend Dependencies
```bash
cd team_03-dev/backend
npm install
```

### Frontend Dependencies
```bash
cd team_03-dev/frontend
npm install
```

## Step 2: Configure Environment Variables

1. Navigate to the backend directory:
   ```bash
   cd team_03-dev/backend
   ```

2. Open the `.env` file and update the following:
   - `MONGO_URI` - Your MongoDB connection string
   - `JWT_SECRET` - A strong random string (min 32 characters)
   - `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET` - Cloudinary credentials
   - `EMAIL_USER`, `EMAIL_PASS` - Email credentials (for Gmail, use App Password)

   See `backend/ENV_SETUP.md` for detailed instructions.

## Step 3: Start MongoDB

### Option A: Local MongoDB
Make sure MongoDB is running on your system:
```bash
# Windows (if MongoDB is installed as a service, it should start automatically)
# Or start manually:
mongod
```

### Option B: MongoDB Atlas
No local setup needed - just use your Atlas connection string in `.env`

## Step 4: Run the Backend Server

Open a terminal and run:
```bash
cd team_03-dev/backend

# For development (with auto-reload):
npm run dev

# OR for production:
npm start
```

The backend server will start on **http://localhost:5000** (or the port specified in your `.env` file).

You should see:
```
MongoDB Connected: ...
Server running on port 5000
```

## Step 5: Run the Frontend

Open a **new terminal** (keep the backend running) and run:
```bash
cd team_03-dev/frontend
npm run dev
```

The frontend will start on **http://localhost:5173** (or another port if 5173 is busy).

You should see:
```
  VITE v7.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

## Step 6: Access the Application

1. Open your browser and go to: **http://localhost:5173**
2. You should see the landing page
3. Navigate to `/login` to sign in or sign up

## Quick Start Commands Summary

### Terminal 1 - Backend:
```bash
cd team_03-dev/backend
npm install          # First time only
npm run dev
```

### Terminal 2 - Frontend:
```bash
cd team_03-dev/frontend
npm install          # First time only
npm run dev
```

## Troubleshooting

### Backend Issues

**Error: Cannot connect to MongoDB**
- Check your `MONGO_URI` in `.env`
- Make sure MongoDB is running (if using local)
- Verify your MongoDB Atlas credentials (if using Atlas)

**Error: Port already in use**
- Change `PORT` in `.env` to a different port (e.g., 5001)
- Or stop the process using port 5000

**Error: Missing environment variables**
- Make sure `.env` file exists in `backend/` directory
- Check that all required variables are set

### Frontend Issues

**Error: Cannot connect to backend**
- Make sure backend is running on port 5000
- Check CORS settings in `backend/server.js`
- Verify the API URL in frontend code matches your backend port

**Error: Port 5173 already in use**
- Vite will automatically use the next available port (5174, 5175, etc.)
- Or specify a port: `npm run dev -- --port 3000`

## Production Build

### Build Frontend:
```bash
cd team_03-dev/frontend
npm run build
```

The built files will be in `frontend/dist/` directory.

### Preview Production Build:
```bash
cd team_03-dev/frontend
npm run preview
```

## Available Scripts

### Backend Scripts:
- `npm start` - Run server in production mode
- `npm run dev` - Run server in development mode (with auto-reload)

### Frontend Scripts:
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Need Help?

- Check `backend/ENV_SETUP.md` for environment variable setup
- Check console logs for error messages
- Verify all dependencies are installed: `npm list`


