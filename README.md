# monk-mode-homepage
Landing page for the app VIMAYA.

## 🚀 Quick Start

This repository contains the landing page for VIMAYA, designed to be hosted on GitHub Pages with optional Cloudflare custom domain integration.

## 📁 Files

- `index.html` - Main landing page
- `styles.css` - Stylesheet for the landing page
- `.github/workflows/pages.yml` - GitHub Actions workflow for automatic deployment
- `CNAME.template` - Template for custom domain configuration

## 🌐 GitHub Pages Setup

### Step 1: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select:
   - Source: **GitHub Actions**
4. The site will automatically deploy when you push to the `main` branch

Your site will be available at: `https://<username>.github.io/monk-mode-homepage/`

### Step 2: Verify Deployment

1. Go to the **Actions** tab in your repository
2. Check that the "Deploy to GitHub Pages" workflow runs successfully
3. Once completed, visit your GitHub Pages URL to see the live site

## 🔗 Custom Domain with Cloudflare

### Step 1: Prepare Domain Configuration

1. Rename `CNAME.template` to `CNAME`
2. Edit the `CNAME` file and replace the content with your domain name:
   ```
   yourdomain.com
   ```
   or
   ```
   www.yourdomain.com
   ```

### Step 2: Configure Cloudflare DNS

1. Log in to your [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Select your domain
3. Go to **DNS** → **Records**
4. Add the following DNS records:

   **For apex domain (yourdomain.com):**
   ```
   Type: A
   Name: @
   Content: 185.199.108.153
   Proxy status: DNS only (gray cloud)
   
   Type: A
   Name: @
   Content: 185.199.109.153
   Proxy status: DNS only (gray cloud)
   
   Type: A
   Name: @
   Content: 185.199.110.153
   Proxy status: DNS only (gray cloud)
   
   Type: A
   Name: @
   Content: 185.199.111.153
   Proxy status: DNS only (gray cloud)
   ```

   **For www subdomain:**
   ```
   Type: CNAME
   Name: www
   Content: <username>.github.io
   Proxy status: DNS only (gray cloud)
   ```

5. Wait for DNS propagation (can take up to 48 hours, usually much faster)

### Step 3: Configure GitHub Pages for Custom Domain

1. Go to repository **Settings** → **Pages**
2. Under **Custom domain**, enter your domain name
3. Click **Save**
4. Wait for DNS check to complete (shows a checkmark when ready)
5. Check **Enforce HTTPS** (after DNS check passes)

### Step 4: Enable Cloudflare Proxy (Optional)

Once GitHub Pages shows your custom domain is working:

1. Return to Cloudflare DNS settings
2. Change **Proxy status** from "DNS only" to "Proxied" (orange cloud)
3. This enables Cloudflare's CDN, DDoS protection, and other features

## 🔧 Local Development

To view the page locally:

1. Clone the repository:
   ```bash
   git clone https://github.com/<username>/monk-mode-homepage.git
   cd monk-mode-homepage
   ```

2. Open `index.html` in your web browser, or use a simple HTTP server:
   ```bash
   # Using Python 3
   python3 -m http.server 8000
   
   # Using Python 2
   python -m SimpleHTTPServer 8000
   
   # Using Node.js
   npx http-server
   ```

3. Visit `http://localhost:8000` in your browser

## 📝 Customization

- Edit `index.html` to change the content
- Modify `styles.css` to adjust the styling
- All changes pushed to `main` branch will automatically deploy via GitHub Actions

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
