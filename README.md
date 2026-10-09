# West Wave Immigration website

Static single-page site (no build step). `index.html` + `assets/` is the whole site.

## Deploy on Hostinger

**Option A: Git (auto-deploy)**
1. hPanel → Websites → Manage → Advanced → **Git**.
2. Repository: `https://github.com/Mesumraza08-art/westwave.git`, Branch: `main`, Directory: leave empty (deploys to `public_html`).
3. Click **Create**, then **Deploy**. Enable **Auto Deployment** and add the webhook URL to GitHub (Settings → Webhooks) to redeploy on every push.

`public_html` must be empty before the first Git deploy (delete the default `default.php`/`index.php`).

**Option B: File Manager**
Upload `index.html`, `.htaccess`, `robots.txt` and the `assets/` folder into `public_html`.

## What `.htaccess` does
- Forces HTTPS and the non-www domain.
- 301-redirects old WordPress URLs (e.g. `/federal-skilled-worker/`) to the matching in-page route (`/#/federal-skilled-worker/`).
- Gzip compression, long cache for images, no cache for HTML.

See `CHECKLIST.md` for content items to confirm before launch.
