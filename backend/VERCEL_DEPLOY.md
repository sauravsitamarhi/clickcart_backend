# Vercel Deployment Guide

## ✅ Updated Files for Vercel

1. **vercel.json** - Updated for modern Vercel deployment
2. **server.js** - Updated to work with Vercel serverless functions

## 🚀 Deploy Backend to Vercel

### Step 1: Install Vercel CLI (if not installed)
```bash
npm install -g vercel
```

### Step 2: Login to Vercel
```bash
vercel login
```

### Step 3: Deploy from Backend Folder
```bash
cd backend
vercel
```

### Step 4: Set Environment Variables

In Vercel Dashboard:
1. Go to your project → Settings → Environment Variables
2. Add these variables:

```
MONGO_URI = mongodb+srv://sauravsitamarhi123_db_user:7i4xQwqUnkiCLp1E@cluster0.fiqzyz6.mongodb.net/clickcart?retryWrites=true&w=majority
JWT_SECRET = your-super-secret-jwt-key-change-this-in-production-12345
NODE_ENV = production
```

### Step 5: Redeploy
After adding environment variables, redeploy:
```bash
vercel --prod
```

## 📝 Vercel Configuration

The `vercel.json` file is configured to:
- Use `@vercel/node` runtime
- Route `/api/*` requests to server.js
- Handle all routes through the Express app

## 🔗 API Endpoints After Deployment

Your API will be available at:
```
https://your-project-name.vercel.app/api/register
https://your-project-name.vercel.app/api/login
https://your-project-name.vercel.app/api/dashboard
https://your-project-name.vercel.app/api/health
```

## ⚙️ Update Frontend API URL

After deploying backend, update frontend `.env` or `authContext.jsx`:

```javascript
const API_URL = import.meta.env.VITE_API_URL || 'https://your-project-name.vercel.app/api';
```

## 🐛 Troubleshooting

### MongoDB Connection Issues
- Make sure MongoDB Atlas allows connections from Vercel IPs
- Add `0.0.0.0/0` to MongoDB Atlas Network Access (for development)

### Environment Variables
- Double-check all env vars are set in Vercel dashboard
- Redeploy after adding env vars

### CORS Issues
- CORS is already configured in server.js
- Make sure frontend URL is allowed

## 📦 Project Structure for Vercel

```
backend/
├── vercel.json          ✅ Vercel configuration
├── server.js            ✅ Main server file
├── package.json         ✅ Dependencies
├── models/             ✅ MongoDB models
├── routes/             ✅ API routes
└── middleware/         ✅ Auth middleware
```

## ✅ Deployment Checklist

- [ ] Vercel CLI installed
- [ ] Logged in to Vercel
- [ ] Environment variables set in Vercel dashboard
- [ ] MongoDB Atlas network access configured
- [ ] Backend deployed successfully
- [ ] Frontend API URL updated
- [ ] Test API endpoints

