# Jackson Wholesale - Deployment Guide

## Project Overview
This is a complete React 19 + Tailwind CSS 4 + Framer Motion website for Jackson Wholesale Distributors Ltd, featuring:
- 10 phone product catalog with hover effects
- 5-step application form
- Enhanced payment calculator with daily/weekly breakdown
- Social proof badges
- Trust & security section
- Location & store hours
- Blog/resources section
- Responsive design for all devices

## Prerequisites
- Node.js 18+ and npm/pnpm
- Git (for version control)
- cPanel hosting with Node.js support OR GitHub Pages

## Local Development

### 1. Install Dependencies
```bash
cd jackson-wholesale-clone
pnpm install
```

### 2. Run Development Server
```bash
pnpm dev
```
The site will be available at `http://localhost:3000`

### 3. Build for Production
```bash
pnpm build
```

## Deployment Options

### Option A: GitHub Pages (Static Site)
1. Push to GitHub:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/jackson-wholesale.git
git push -u origin main
```

2. Enable GitHub Pages in repository settings
3. Set source to `main` branch, `/dist` folder

### Option B: cPanel with Node.js

1. **Upload Files**
   - Extract `jackson-wholesale-complete.zip` to your cPanel file manager
   - Or use SSH: `scp -r jackson-wholesale-clone user@host:/home/user/public_html/`

2. **Install Dependencies**
```bash
cd ~/public_html/jackson-wholesale-clone
pnpm install
```

3. **Build the Project**
```bash
pnpm build
```

4. **Configure Node.js App in cPanel**
   - Go to Setup Node.js App
   - Create new app pointing to `/home/user/public_html/jackson-wholesale-clone`
   - Set startup file to `dist/index.js`
   - Set environment to `production`

5. **Set Environment Variables** (if needed)
   - Add any custom secrets in cPanel Node.js app settings

### Option C: Vercel (Recommended for Static)
1. Connect your GitHub repository to Vercel
2. Set build command: `pnpm build`
3. Set output directory: `dist`
4. Deploy automatically on push

### Option D: Netlify
1. Connect GitHub repository
2. Build settings:
   - Build command: `pnpm build`
   - Publish directory: `dist`
3. Deploy

## Environment Variables
No environment variables required for basic deployment. The app works out of the box.

## Customization

### Update Company Info
Edit `client/src/const.ts`:
```typescript
export const WHATSAPP_NUMBER = "256768980819"; // Your WhatsApp number
export const DISPLAY_PHONE = "+256 768 980 819";
```

### Update Phone Catalog
Edit `client/src/pages/Home.tsx` - `PHONES` array (lines 65-200)

### Update Colors
Edit `client/src/index.css` - CSS variables in `:root` section

### Update Content
Edit `client/src/pages/Home.tsx` - All section components

## Troubleshooting

### Build Errors
```bash
# Clear cache and reinstall
rm -rf node_modules pnpm-lock.yaml
pnpm install
pnpm build
```

### Port Already in Use
```bash
# Use different port
pnpm dev -- --port 3001
```

### TypeScript Errors
```bash
# Check for type errors
pnpm check
```

## Performance Optimization

1. **Images**: All images use optimized storage URLs
2. **Lazy Loading**: Sections use Framer Motion's `whileInView` for lazy loading
3. **Code Splitting**: React automatically splits components

## Security

- SSL certificate recommended for production
- WhatsApp integration is client-side only
- No sensitive data stored in frontend
- All form submissions go through WhatsApp

## Support

For issues or customization:
1. Check TypeScript errors: `pnpm check`
2. Review browser console for errors
3. Ensure all dependencies are installed: `pnpm install`

## License
All rights reserved - Jackson Wholesale Distributors Ltd
