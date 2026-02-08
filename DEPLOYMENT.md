# Deployment Guide: Git + Vercel Workflow

## Repository Information

**GitHub Repository:** https://github.com/1GMedia/refined-craft-landing

**Structure:**
```
refined-craft-landing/
├── variant-a-editorial/    # Editorial design variant
├── variant-b-brutalist/    # Brutalist design variant
├── variant-c-gradient/     # Gradient design variant
├── variant-switcher.html   # Comparison tool
├── images/                 # Shared images
└── .gitignore             # Excludes .vercel/ directories
```

---

## Vercel Deployment Setup

### Option 1: Deploy All Three Variants (Recommended)

Create **three separate Vercel projects** to deploy each variant independently:

#### 1. Variant A (Editorial)
```bash
cd ~/clawd/projects/refined-craft-landing
vercel --name refined-craft-editorial --prod
# When prompted for root directory, enter: variant-a-editorial
```

#### 2. Variant B (Brutalist)
```bash
cd ~/clawd/projects/refined-craft-landing
vercel --name refined-craft-brutalist --prod
# When prompted for root directory, enter: variant-b-brutalist
```

#### 3. Variant C (Gradient)
```bash
cd ~/clawd/projects/refined-craft-landing
vercel --name refined-craft-gradient --prod
# When prompted for root directory, enter: variant-c-gradient
```

### Option 2: Deploy Switcher for Client Review
```bash
cd ~/clawd/projects/refined-craft-landing
vercel --name refined-craft-switcher --prod
# Root directory: . (project root)
# This deploys the variant-switcher.html for easy comparison
```

---

## GitHub ↔ Vercel Integration

### Connect GitHub Repository to Vercel

1. **Via Vercel Dashboard:**
   - Go to https://vercel.com/dashboard
   - Click "Add New..." → "Project"
   - Import from GitHub: `1GMedia/refined-craft-landing`
   - Configure each project with its respective root directory:
     - **Editorial:** `variant-a-editorial`
     - **Brutalist:** `variant-b-brutalist`
     - **Gradient:** `variant-c-gradient`

2. **Automatic Deployments:**
   - Every push to `main` branch triggers production deployment
   - Pull requests create preview deployments automatically
   - No build step needed (pure HTML/CSS)

---

## Git Workflow

### Making Changes

```bash
cd ~/clawd/projects/refined-craft-landing

# Edit files in any variant directory
# Example: variant-a-editorial/styles.css

# Stage changes
git add .

# Commit with descriptive message
git commit -m "Update: [description of changes]"

# Push to GitHub (triggers Vercel deployment)
git push origin main
```

### Creating Feature Branches

```bash
# Create and switch to new branch
git checkout -b feature/new-hero-section

# Make changes, commit
git add .
git commit -m "Add new hero section animation"

# Push branch (creates preview deployment on Vercel)
git push origin feature/new-hero-section

# Merge via GitHub Pull Request
# After review, merge to main → production deployment
```

---

## Vercel Configuration

### Project Settings (vercel.json - optional)

If you need custom configuration, create `vercel.json` in each variant directory:

```json
{
  "buildCommand": null,
  "outputDirectory": ".",
  "framework": null,
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=3600, must-revalidate"
        }
      ]
    }
  ]
}
```

---

## Environment-Specific Workflows

### Development Preview
- **Push to any branch** → Vercel creates preview URL
- Share preview URL for client feedback before merging

### Production Deployment
- **Merge to main** → Automatic production deployment
- All three variants update independently

### Rollback
```bash
# Via Vercel Dashboard: Deployments → Select previous deployment → Promote to Production

# Via Git:
git revert <commit-hash>
git push origin main
```

---

## Next Steps

### 1. Connect GitHub to Vercel
- Import repository from Vercel dashboard
- Create 3 separate projects (one per variant)
- Configure root directories

### 2. Set Up Custom Domains (Optional)
- editorial.refinedcraft.ai
- brutalist.refinedcraft.ai  
- gradient.refinedcraft.ai

### 3. Enable Analytics
- Vercel Analytics for visitor tracking
- A/B testing between variants

### 4. Add Environment Variables (If Needed)
- Contact forms
- Analytics keys
- Feature flags

---

## Troubleshooting

### Issue: `.vercel` directories not ignored
**Solution:** Already handled via `.gitignore` at project root

### Issue: Vercel not detecting changes
**Solution:** Check root directory setting in Vercel project settings

### Issue: Images not loading
**Solution:** Use relative paths (`./images/`) or copy images to each variant directory

---

## Quick Reference Commands

```bash
# Check git status
git status

# View commit history
git log --oneline

# Pull latest changes
git pull origin main

# Create new branch
git checkout -b branch-name

# Deploy to Vercel manually
vercel --prod

# View Vercel deployments
vercel ls
```

---

**Repository URL:** https://github.com/1GMedia/refined-craft-landing

Ready for Vercel integration! 🚀
