# Vercel Quick Start Guide

## ✅ GitHub Setup Complete

**Repository URL:** https://github.com/1GMedia/refined-craft-landing

All code has been pushed and is ready for Vercel integration.

---

## 🚀 Next Steps: Connect to Vercel

### Option 1: Via Vercel Dashboard (Recommended)

1. **Go to Vercel Dashboard**  
   → https://vercel.com/dashboard

2. **Import Repository**  
   - Click "Add New..." → "Project"
   - Select "Import Git Repository"
   - Choose: `1GMedia/refined-craft-landing`

3. **Create 3 Separate Projects**  
   Deploy each variant as an independent project:

   | Project Name | Root Directory | Purpose |
   |--------------|----------------|---------|
   | `refined-craft-editorial` | `variant-a-editorial` | Editorial design |
   | `refined-craft-brutalist` | `variant-b-brutalist` | Brutalist design |
   | `refined-craft-gradient` | `variant-c-gradient` | Gradient design |

4. **Configure Each Project**
   - **Framework Preset:** None (static HTML)
   - **Build Command:** (leave empty)
   - **Output Directory:** `.` (or leave empty)
   - **Root Directory:** (see table above)

5. **Deploy**  
   Click "Deploy" for each project → Vercel will build and deploy automatically

---

### Option 2: Via Vercel CLI

```bash
cd ~/clawd/projects/refined-craft-landing

# Deploy Editorial variant
vercel --name refined-craft-editorial --prod
# When prompted, set root directory: variant-a-editorial

# Deploy Brutalist variant
vercel --name refined-craft-brutalist --prod
# When prompted, set root directory: variant-b-brutalist

# Deploy Gradient variant
vercel --name refined-craft-gradient --prod
# When prompted, set root directory: variant-c-gradient
```

---

## 🔄 Automatic Deployment Flow

Once connected to Vercel:

- **Push to `main`** → Production deployment
- **Open Pull Request** → Preview deployment (shareable URL)
- **Merge PR** → Automatic production update

---

## 📋 What's Included

✅ Git repository initialized  
✅ `.gitignore` configured (excludes `.vercel/` directories)  
✅ All 3 variants committed and pushed  
✅ Variant switcher for easy comparison  
✅ Documentation: `DEPLOYMENT.md` with full workflow  
✅ GitHub repository created and configured

---

## 🎯 Recommended Workflow

1. **Connect to Vercel** (via dashboard - takes 5 minutes)
2. **Get your live URLs** (Vercel provides production URLs immediately)
3. **Share with client** for feedback
4. **Make updates** via Git → Push → Auto-deploy

---

## 📞 Support Resources

- **Full Deployment Guide:** See `DEPLOYMENT.md` in repo
- **Vercel Docs:** https://vercel.com/docs
- **GitHub Repository:** https://github.com/1GMedia/refined-craft-landing

---

Ready to deploy! 🎉
