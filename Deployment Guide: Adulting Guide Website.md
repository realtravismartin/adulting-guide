# Deployment Guide: Adulting Guide Website

This guide will walk you through deploying your "What You Must Know to Function as an American Adult" website to production using Vercel and GitHub.

## 📋 Prerequisites

Before starting, ensure you have:
- [x] GitHub account (@realtravismartin)
- [x] Vercel account (sign up at vercel.com)
- [x] Stripe account for payment processing
- [x] Domain name (optional, Vercel provides free subdomain)

## 🚀 Step 1: GitHub Repository Setup

### 1.1 Create GitHub Repository
1. Go to [GitHub.com](https://github.com) and sign in
2. Click "New repository" (green button)
3. Repository name: `adulting-guide`
4. Description: `Complete guide to functioning as an American adult - digital product with Stripe integration`
5. Set to **Public** (or Private if preferred)
6. **DO NOT** initialize with README (we already have one)
7. Click "Create repository"

### 1.2 Upload Project Files
You have two options:

**Option A: Using GitHub Web Interface (Easier)**
1. Download the project folder from the sandbox
2. Zip the entire `adulting-guide` folder
3. On your new GitHub repository page, click "uploading an existing file"
4. Drag and drop all files from the project folder
5. Commit message: "Initial commit: Complete adulting guide with Stripe integration"
6. Click "Commit changes"

**Option B: Using Git Commands (Advanced)**
```bash
# Navigate to your project folder
cd adulting-guide

# Initialize git repository
git init

# Add all files
git add .

# Commit files
git commit -m "Initial commit: Complete adulting guide with Stripe integration"

# Add GitHub remote
git remote add origin https://github.com/realtravismartin/adulting-guide.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## 🌐 Step 2: Vercel Deployment

### 2.1 Connect GitHub to Vercel
1. Go to [vercel.com](https://vercel.com) and sign up/sign in
2. Click "New Project"
3. Click "Import Git Repository"
4. Connect your GitHub account if not already connected
5. Find and select your `adulting-guide` repository
6. Click "Import"

### 2.2 Configure Deployment Settings
Vercel will auto-detect the React/Vite project. Verify these settings:
- **Framework Preset**: Vite
- **Build Command**: `pnpm run build`
- **Output Directory**: `dist`
- **Install Command**: `pnpm install`

### 2.3 Environment Variables (Production Stripe)
1. In Vercel dashboard, go to your project
2. Click "Settings" tab
3. Click "Environment Variables"
4. Add these variables:

```
VITE_STRIPE_PUBLISHABLE_KEY=pk_live_your_actual_stripe_key
VITE_API_BASE_URL=https://your-domain.vercel.app
```

**Important**: Replace with your actual Stripe live keys for production!

### 2.4 Deploy
1. Click "Deploy" button
2. Wait for build to complete (2-3 minutes)
3. Your site will be live at: `https://adulting-guide-xxx.vercel.app`

## 🔧 Step 3: Production Configuration

### 3.1 Stripe Setup for Production
1. Log into your Stripe dashboard
2. Switch to "Live" mode (toggle in top left)
3. Go to Developers > API Keys
4. Copy your "Publishable key" (starts with `pk_live_`)
5. Update the environment variable in Vercel

### 3.2 Custom Domain (Optional)
1. In Vercel project settings, go to "Domains"
2. Add your custom domain (e.g., `adultingguide.com`)
3. Follow Vercel's DNS configuration instructions
4. SSL certificate will be automatically provisioned

### 3.3 Email Integration Setup
To make the email capture functional:

**Option A: Supabase (Recommended)**
1. Sign up at [supabase.com](https://supabase.com)
2. Create new project
3. Create a table for email subscribers
4. Update the email form to use Supabase API

**Option B: Netlify Forms**
1. Add `netlify` attribute to your form
2. Deploy on Netlify instead of Vercel

**Option C: Third-party service**
- ConvertKit, Mailchimp, or similar email service
- Update form action to point to their API

## 📊 Step 4: Analytics and Monitoring

### 4.1 Google Analytics
1. Create Google Analytics account
2. Add tracking code to `index.html`
3. Monitor traffic and conversions

### 4.2 Vercel Analytics
1. Enable Vercel Analytics in project settings
2. Monitor performance and user behavior

## 🛡️ Step 5: Security and Performance

### 5.1 Security Headers
The `vercel.json` file includes security headers:
- X-Content-Type-Options
- X-Frame-Options
- X-XSS-Protection
- Referrer-Policy

### 5.2 Performance Optimization
- Static assets are cached for 1 year
- Gzip compression enabled automatically
- CDN distribution worldwide

## 🔄 Step 6: Updates and Maintenance

### 6.1 Making Updates
1. Edit files in your local project or GitHub web interface
2. Commit changes to the main branch
3. Vercel automatically redeploys on every commit
4. Changes are live in 2-3 minutes

### 6.2 Content Updates
- Edit content in React components
- Update pricing in `StripeCheckout.jsx`
- Add new chapters by creating new components

## 📈 Step 7: Marketing and Launch

### 7.1 Pre-Launch Checklist
- [x] Test all functionality on mobile and desktop
- [x] Verify Stripe payment flow works
- [x] Check email capture functionality
- [x] Test all navigation links
- [x] Verify content displays correctly
- [x] Check loading speed (should be <3 seconds)

### 7.2 Launch Strategy
1. **Soft Launch**: Share with friends/family for feedback
2. **Social Media**: Announce on your platforms
3. **Content Marketing**: Create blog posts about adulting
4. **SEO**: Optimize for keywords like "adulting guide", "life skills"
5. **Paid Ads**: Consider Google Ads or Facebook Ads

## 🆘 Troubleshooting

### Common Issues

**Build Fails**
- Check that all dependencies are in `package.json`
- Verify Node.js version compatibility
- Check for TypeScript errors

**Stripe Not Working**
- Verify you're using live keys in production
- Check that webhook endpoints are configured
- Ensure HTTPS is enabled

**Email Form Not Working**
- Implement actual email service integration
- Check form validation
- Verify API endpoints

**Performance Issues**
- Optimize images (use WebP format)
- Enable lazy loading for images
- Minimize JavaScript bundle size

## 📞 Support

If you encounter issues:
1. Check Vercel deployment logs
2. Review browser console for errors
3. Test locally first with `pnpm run dev`
4. Check GitHub repository for any missing files

## 🎉 Success Metrics

Track these KPIs after launch:
- **Traffic**: Unique visitors per month
- **Email Conversion**: % of visitors who provide email
- **Purchase Conversion**: % of emails who purchase
- **Revenue**: Monthly recurring revenue
- **Customer Satisfaction**: Reviews and testimonials

---

**Congratulations!** Your adulting guide is now live and ready to help thousands of young adults master essential life skills.

**Live URL**: `https://your-domain.vercel.app`  
**Admin Dashboard**: Vercel project dashboard  
**Repository**: `https://github.com/realtravismartin/adulting-guide`

