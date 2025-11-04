# Code Mesh - Deployment Guide

This guide will walk you through deploying your Code Mesh project to GitHub and Vercel.

## ✅ Completed Steps

- ✓ Removed original Git history
- ✓ Updated all package.json files with your information
- ✓ Updated README.md, LICENSE, and CONTRIBUTING.md
- ✓ Updated source code files (GitHubCorner.tsx, Footer.tsx)
- ✓ Created .env and .env.example files
- ✓ Initialized fresh Git repository with initial commit

---

## 📦 Step 1: Create GitHub Repository

### Option A: Using GitHub CLI (Recommended)
```bash
# Login to GitHub (if not already logged in)
gh auth login

# Create the repository
gh repo create CodeMesh --public --source=. --remote=origin --push

# The repository will be automatically created and code pushed!
```

### Option B: Using GitHub Website
1. Go to https://github.com/new
2. **Repository name:** `CodeMesh`
3. **Description:** `A modern collaborative coding and chat platform`
4. **Visibility:** Public (or Private if you prefer)
5. **DO NOT** initialize with README, .gitignore, or license (we already have these)
6. Click **"Create repository"**

After creating the repository on GitHub:

```bash
# Add the remote repository
git remote add origin https://github.com/DineshDumka/CodeMesh.git

# Push your code
git push -u origin main
```

---

## 🚀 Step 2: Deploy Frontend to Vercel

### Method 1: Using Vercel CLI (Recommended)

1. **Install Vercel CLI:**
   ```bash
   npm install -g vercel
   ```

2. **Login to Vercel:**
   ```bash
   vercel login
   ```

3. **Deploy the Client (Frontend):**
   ```bash
   cd client
   vercel
   ```

   When prompted:
   - **Set up and deploy:** Yes
   - **Which scope:** Select your account
   - **Link to existing project:** No
   - **Project name:** `code-mesh-client` (or your preferred name)
   - **Directory:** `./` (current directory)
   - **Override settings:** No

4. **Deploy to Production:**
   ```bash
   vercel --prod
   ```

### Method 2: Using Vercel Dashboard

1. Go to https://vercel.com/new
2. Import your GitHub repository: `DineshDumka/CodeMesh`
3. Configure the project:
   - **Framework Preset:** Vite
   - **Root Directory:** `client`
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
4. Add Environment Variables:
   - `VITE_BACKEND_URL` = `<your-backend-url>` (we'll set this after deploying the backend)
5. Click **"Deploy"**

---

## 🔧 Step 3: Deploy Backend to Vercel

### Method 1: Using Vercel CLI

1. **Deploy the Server (Backend):**
   ```bash
   cd ../server
   vercel
   ```

   When prompted:
   - **Set up and deploy:** Yes
   - **Which scope:** Select your account
   - **Link to existing project:** No
   - **Project name:** `code-mesh-server` (or your preferred name)
   - **Directory:** `./` (current directory)
   - **Override settings:** No

2. **Deploy to Production:**
   ```bash
   vercel --prod
   ```

### Method 2: Using Vercel Dashboard

1. Go to https://vercel.com/new
2. Import your GitHub repository again: `DineshDumka/CodeMesh`
3. Configure the project:
   - **Framework Preset:** Other
   - **Root Directory:** `server`
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
   - **Install Command:** `npm install`
4. Add Environment Variables:
   - `PORT` = `3000`
5. Click **"Deploy"**

---

## 🔗 Step 4: Connect Frontend and Backend

After both deployments are complete:

1. **Get your backend URL** from Vercel (e.g., `https://code-mesh-server.vercel.app`)

2. **Update Frontend Environment Variable:**
   - Go to your frontend project on Vercel Dashboard
   - Settings → Environment Variables
   - Add or update: `VITE_BACKEND_URL` = `https://your-backend-url.vercel.app`
   - Redeploy the frontend

3. **Update Backend CORS:**
   - Go to your backend project on Vercel Dashboard
   - Settings → Environment Variables
   - Add: `CORS_ORIGIN` = `https://your-frontend-url.vercel.app`
   - Redeploy the backend

---

## 🔄 Step 5: Update Local .env Files

Update your local environment files for development:

**client/.env:**
```env
# For local development with local backend
VITE_BACKEND_URL=http://localhost:3000

# For local development with production backend (uncomment to use)
# VITE_BACKEND_URL=https://your-backend-url.vercel.app
```

**server/.env:**
```env
PORT=3000

# Add your frontend URL for CORS
CORS_ORIGIN=http://localhost:5173
```

---

## 🧪 Step 6: Test Your Deployment

1. Visit your frontend URL (from Vercel)
2. Create a new room
3. Test all features:
   - Code editing
   - File creation/deletion
   - Code execution
   - Real-time collaboration
   - Chat functionality

---

## 📝 Useful Commands

### Local Development
```bash
# Start backend (from server directory)
npm run dev

# Start frontend (from client directory)
npm run dev
```

### Production Deployment
```bash
# Deploy frontend to production
cd client && vercel --prod

# Deploy backend to production
cd server && vercel --prod
```

### Git Commands
```bash
# Add changes
git add .

# Commit changes
git commit -m "Your commit message"

# Push to GitHub
git push origin main
```

---

## 🎯 Next Steps

1. **Custom Domain (Optional):**
   - Go to Vercel Dashboard → Your Project → Settings → Domains
   - Add your custom domain

2. **Environment Variables:**
   - Add any API keys or secrets needed
   - Never commit `.env` files to Git

3. **Monitoring:**
   - Check Vercel Dashboard for deployment logs
   - Monitor function execution and performance

4. **Updates:**
   - Push changes to GitHub
   - Vercel will automatically redeploy

---

## 🐛 Troubleshooting

### Frontend can't connect to Backend
- Check CORS settings in backend
- Verify `VITE_BACKEND_URL` in frontend environment variables
- Check backend logs on Vercel

### Build Failures
- Check build logs on Vercel Dashboard
- Ensure all dependencies are in package.json
- Verify Node.js version compatibility

### WebSocket Issues
- Vercel supports WebSockets on all plans
- Check Socket.io configuration
- Verify backend URL is correct

---

## 📧 Support

If you encounter any issues:
- Check Vercel documentation: https://vercel.com/docs
- Review deployment logs
- Check GitHub repository issues

---

**Author:** Dinesh Dumka  
**Email:** dineshdumka27@gmail.com  
**Repository:** https://github.com/DineshDumka/CodeMesh
