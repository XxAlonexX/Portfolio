# Portfolio Deployment Guide for Render

## Prerequisites
- GitHub account with your portfolio repository
- Render account (sign up at [render.com](https://render.com))

## Step-by-Step Deployment Process

### 1. Prepare Your Repository
Your repository is already prepared with the necessary configuration files:
- ✅ `render.yaml` - Render configuration
- ✅ `package.json` - Updated with proper build scripts
- ✅ Static site structure ready

### 2. Push to GitHub
Make sure your code is pushed to GitHub:
```bash
git add .
git commit -m "Add Render deployment configuration"
git push origin main
```

### 3. Deploy on Render

#### Option A: Using render.yaml (Recommended)
1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click **"New +"** → **"Static Site"**
3. Connect your GitHub account if not already connected
4. Select your portfolio repository
5. Render will automatically detect the `render.yaml` configuration
6. Click **"Create Static Site"**

#### Option B: Manual Configuration
If you prefer manual setup:
1. Go to [Render Dashboard](https://dashboard.render.com)
2. Click **"New +"** → **"Static Site"**
3. Connect your GitHub repository
4. Configure the following settings:
   - **Name**: `portfolio` (or your preferred name)
   - **Branch**: `main`
   - **Build Command**: `npm install && npm run build`
   - **Publish Directory**: `dist`
   - **Node Version**: `18` (or latest LTS)

### 4. Environment Variables (Optional)
If you need any environment variables:
1. Go to your service dashboard
2. Navigate to **"Environment"** tab
3. Add any required variables

### 5. Custom Domain (Optional)
To use a custom domain:
1. Go to your service dashboard
2. Navigate to **"Settings"** tab
3. Scroll to **"Custom Domains"**
4. Add your domain and follow DNS instructions

## Configuration Details

### render.yaml
The configuration file includes:
- **Build Command**: `npm install && npm run build`
- **Publish Directory**: `./dist` (Astro's default output)
- **Security Headers**: X-Frame-Options, X-Content-Type-Options, etc.
- **Caching**: Optimized caching for static assets

### package.json Updates
- **start script**: Changed to `astro preview` for production
- **build script**: Uses `astro build` to generate static files

## Build Process
1. Render installs dependencies (`npm install`)
2. Builds the static site (`npm run build`)
3. Serves files from the `dist` directory
4. Applies security headers and caching rules

## Troubleshooting

### Common Issues:
1. **Build Fails**: Check Node.js version (use 18+)
2. **404 Errors**: Verify `dist` directory is being published
3. **Assets Not Loading**: Check file paths in `public/assets/`

### Debug Steps:
1. Check build logs in Render dashboard
2. Verify all dependencies are in `package.json`
3. Test build locally: `npm run build`

## Performance Optimizations
- Static assets are cached for 1 year
- Security headers are applied
- Gzip compression is enabled by default
- CDN distribution is automatic

## Monitoring
- View deployment logs in Render dashboard
- Monitor performance metrics
- Set up alerts for build failures

## Cost
- **Free Tier**: 750 hours/month
- **Paid Plans**: Start at $7/month for always-on hosting

Your portfolio should be live at: `https://your-app-name.onrender.com`
