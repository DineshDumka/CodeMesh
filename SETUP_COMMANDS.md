# Quick Setup Commands

## 🚀 Quick Start - Push to GitHub

Run these commands in your terminal from the project root:

```powershell
# Navigate to project directory (if not already there)
cd c:\Users\Dinesh\Desktop\code-mesh\code-mesh-clone

# Add GitHub remote
git remote add origin https://github.com/DineshDumka/CodeMesh.git

# Push to GitHub
git push -u origin main
```

---

## 📦 Alternative: Using GitHub CLI (Fastest Method)

If you have GitHub CLI installed:

```powershell
# Create repo and push in one command
gh repo create CodeMesh --public --source=. --remote=origin --push
```

If you don't have GitHub CLI, install it:
```powershell
winget install --id GitHub.cli
```

---

## 🔍 Verify Repository Setup

After pushing, verify your remote:

```powershell
git remote -v
```

Expected output:
```
origin  https://github.com/DineshDumka/CodeMesh.git (fetch)
origin  https://github.com/DineshDumka/CodeMesh.git (push)
```

---

## 🚀 Deploy to Vercel

### Install Vercel CLI:
```powershell
npm install -g vercel
```

### Login to Vercel:
```powershell
vercel login
```

### Deploy Frontend:
```powershell
cd client
vercel --prod
```

### Deploy Backend:
```powershell
cd ..\server
vercel --prod
```

---

## ✅ What's Been Done

All personalizations complete:
- ✓ Fresh Git repository initialized
- ✓ All references to original author removed
- ✓ Your name, email, and GitHub links updated everywhere
- ✓ Package.json files updated with your details
- ✓ README, LICENSE, and CONTRIBUTING updated
- ✓ Environment files created (.env and .env.example)
- ✓ Source code updated with your GitHub profile
- ✓ Initial commit created with your credentials

---

## 📝 Next Steps

1. **Create GitHub Repository** (if not using CLI):
   - Go to: https://github.com/new
   - Name: `CodeMesh`
   - Description: `A modern collaborative coding and chat platform`
   - Public repository
   - Don't initialize with README
   - Click "Create repository"

2. **Push your code** (use commands above)

3. **Deploy to Vercel** (see DEPLOYMENT_GUIDE.md for detailed steps)

4. **Configure environment variables** on Vercel after deployment

---

For detailed deployment instructions, see **DEPLOYMENT_GUIDE.md**
