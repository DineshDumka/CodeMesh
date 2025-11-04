# 🚀 Vercel Deployment - Step by Step Guide

Your GitHub repository is now ready! Follow these steps to deploy to Vercel.

---

## 📋 Prerequisites

✅ GitHub repository pushed: https://github.com/DineshDumka/CodeMesh
✅ Vercel account needed: https://vercel.com (sign up with GitHub)

---

## 🎯 Deployment Order

**IMPORTANT:** Deploy in this order:
1. Backend Server first (to get the API URL)
2. Frontend Client second (using the backend URL)

---

## 🔧 Step 1: Deploy Backend Server

### Option A: Using Vercel Dashboard (Recommended for First Deployment)

1. **Go to Vercel:**
   - Visit: https://vercel.com/new
   - Sign in with your GitHub account

2. **Import Repository:**
   - Click "Add New..." → "Project"
   - Select `DineshDumka/CodeMesh` from your repositories
   - Click "Import"

3. **Configure Backend Project:**
   ```
   Project Name: code-mesh-server
   Framework Preset: Other
   Root Directory: server
   Build Command: npm run build
   Output Directory: dist
   Install Command: npm install
   ```

4. **Add Environment Variables:**
   ```
   PORT = 3000
   ```

5. **Click "Deploy"**

6. **IMPORTANT - Copy Your Backend URL:**
   - After deployment, you'll get a URL like: `https://code-mesh-server.vercel.app`
   - **Save this URL** - you'll need it for the frontend!

---

## 🎨 Step 2: Deploy Frontend Client

1. **Create New Project on Vercel:**
   - Go to: https://vercel.com/new
   - Import the SAME repository: `DineshDumka/CodeMesh`

2. **Configure Frontend Project:**
   ```
   Project Name: code-mesh-client
   Framework Preset: Vite
   Root Directory: client
   Build Command: npm run build
   Output Directory: dist
   Install Command: npm install
   ```

3. **Add Environment Variables:**
   ```
   VITE_BACKEND_URL = https://code-mesh-server.vercel.app
   ```
   ⚠️ Use the EXACT backend URL from Step 1!

4. **Click "Deploy"**

5. **Copy Your Frontend URL:**
   - You'll get a URL like: `https://code-mesh-client.vercel.app`

---

## 🔗 Step 3: Connect Frontend and Backend (CORS)

1. **Update Backend Environment Variables:**
   - Go to your backend project on Vercel
   - Settings → Environment Variables
   - Add new variable:
     ```
     CORS_ORIGIN = https://code-mesh-client.vercel.app
     ```
   - Use the EXACT frontend URL from Step 2!

2. **Redeploy Backend:**
   - Go to Deployments tab
   - Click the three dots (...) on the latest deployment
   - Click "Redeploy"
   - Or push a new commit to trigger automatic redeployment

---

## ✅ Step 4: Verify Deployment

1. **Test Frontend:**
   - Visit: `https://code-mesh-client.vercel.app`
   - You should see the homepage
   - Try creating a room

2. **Test Connection:**
   - Create a room with username
   - If you can join successfully, backend is working!

3. **Test Collaboration:**
   - Open two browser tabs
   - Join same room with different usernames
   - Type code - should sync in real-time

---

## 🐛 Troubleshooting

### Issue: "Failed to connect to server"
**Solution:**
- Verify `VITE_BACKEND_URL` in frontend environment variables
- Check backend is deployed and running
- Verify CORS_ORIGIN in backend matches frontend URL exactly
- Redeploy backend after changing CORS

### Issue: Build Failed
**Solution:**
- Check build logs on Vercel
- Ensure all dependencies are in package.json
- Try running `npm run build` locally first

### Issue: WebSocket Connection Failed
**Solution:**
- Vercel supports WebSockets on all plans
- Verify Socket.io configuration
- Check backend logs on Vercel

---

## 📱 Using Custom Domains (Optional)

1. Go to Project Settings → Domains
2. Add your custom domain
3. Update environment variables with new domain
4. Redeploy both projects

---

## 🔄 Future Updates

When you make changes to your code:

1. **Commit and Push to GitHub:**
   ```bash
   git add .
   git commit -m "Your changes"
   git push origin main
   ```

2. **Vercel Auto-Deploy:**
   - Vercel automatically deploys when you push to main branch
   - Monitor deployments on Vercel dashboard

3. **Manual Redeploy:**
   - Go to Deployments tab on Vercel
   - Click "Redeploy" on any previous deployment

---

## 📊 Environment Variables Reference

### Backend (code-mesh-server)
```env
PORT=3000
CORS_ORIGIN=https://code-mesh-client.vercel.app
```

### Frontend (code-mesh-client)
```env
VITE_BACKEND_URL=https://code-mesh-server.vercel.app
```

---

## 🎯 Quick Links

- **Vercel Dashboard:** https://vercel.com/dashboard
- **GitHub Repository:** https://github.com/DineshDumka/CodeMesh
- **Backend Deployment:** (You'll get this URL after deploying)
- **Frontend Deployment:** (You'll get this URL after deploying)

---

## ✨ Success Checklist

Before going live:

- [ ] Backend deployed successfully
- [ ] Frontend deployed successfully
- [ ] CORS configured correctly
- [ ] Environment variables set
- [ ] Can create and join rooms
- [ ] Real-time collaboration works
- [ ] Chat functionality works
- [ ] Code execution works
- [ ] File operations work

---

## 🎉 You're Ready!

Follow these steps carefully, and your Code Mesh will be live in minutes!

**Good luck with your deployment! 🚀**
