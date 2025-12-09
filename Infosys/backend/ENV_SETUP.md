# Environment Variables Setup Guide

This guide will help you set up the `.env` file for the backend server.

## Quick Start

1. Copy `.env.example` to `.env` (if not already done):
   ```bash
   cp .env.example .env
   ```

2. Open the `.env` file and fill in the required values (see below).

## Required Environment Variables

### 1. Server Configuration
```env
PORT=5000
NODE_ENV=development
```
- `PORT`: The port number for the server (default: 5000)
- `NODE_ENV`: Environment mode (development/production)

### 2. MongoDB Database
```env
MONGO_URI=mongodb://localhost:27017/cleanstreet
```
**Options:**
- **Local MongoDB**: `mongodb://localhost:27017/cleanstreet`
- **MongoDB Atlas**: `mongodb+srv://username:password@cluster.mongodb.net/database-name?retryWrites=true&w=majority`

**To get MongoDB Atlas connection string:**
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free cluster
3. Get your connection string from the "Connect" button
4. Replace `<password>` with your database password

### 3. JWT Secret Key
```env
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production-min-32-chars
```
- Generate a strong random string (minimum 32 characters)
- You can use: `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`
- **Important**: Change this in production!

### 4. Cloudinary Configuration (for image uploads)
```env
CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret
```
**To get Cloudinary credentials:**
1. Sign up at [Cloudinary](https://cloudinary.com)
2. Go to Dashboard
3. Copy your Cloud Name, API Key, and API Secret

### 5. Email Configuration (for sending emails)
```env
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password-here
```
**For Gmail:**
1. Enable 2-Factor Authentication on your Google account
2. Go to [Google App Passwords](https://myaccount.google.com/apppasswords)
3. Generate an App Password for "Mail"
4. Use the 16-character password (not your regular Gmail password)
5. Use your Gmail address for `EMAIL_USER`

**Note:** The App Password is a 16-character code without spaces.

## Example .env File

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Database Connection
MONGO_URI=mongodb+srv://user:password@cluster0.xxxxx.mongodb.net/cleanstreet?retryWrites=true&w=majority

# JWT Secret Key
JWT_SECRET=a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2w3x4y5z6

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=my-cloud-name
CLOUDINARY_API_KEY=123456789012345
CLOUDINARY_API_SECRET=abcdefghijklmnopqrstuvwxyz123456

# Email Configuration
EMAIL_USER=myemail@gmail.com
EMAIL_PASS=abcd efgh ijkl mnop
```

## Verification

After setting up your `.env` file, start the server:
```bash
npm start
# or
npm run dev
```

The server should connect to MongoDB and start without errors. If you see connection errors, double-check your `MONGO_URI`.

## Security Notes

- ⚠️ **Never commit `.env` file to version control** (it's already in `.gitignore`)
- ⚠️ Use different values for development and production
- ⚠️ Keep your JWT_SECRET secure and random
- ⚠️ Don't share your `.env` file publicly

