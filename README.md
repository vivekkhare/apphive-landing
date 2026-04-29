# Apphive landing site

Static one-page site at https://apphive.co.in

## Files
- `index.html` — single-page landing with apps, about, privacy, contact, and AdSense slots
- `ads.txt` — AdSense authorisation
- `CNAME` — tells GitHub Pages to serve at `apphive.co.in`
- `robots.txt` / `sitemap.xml` — for search engines
- `.github/workflows/deploy.yml` — auto-deploys on push to `main`

## Deploy steps

1. Create a new GitHub repo (e.g. `apphive-site`), make it public.
2. Push this folder as the repo root:
   ```bash
   cd apphive-landing
   git init -b main
   git add .
   git commit -m "Apphive landing site"
   git remote add origin https://github.com/<you>/apphive-site.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages → Source: GitHub Actions**, **Custom domain: apphive.co.in**, **Enforce HTTPS** (after DNS propagates).
4. Update DNS at your registrar — add A records on the apex pointing to GitHub:
   ```
   apphive.co.in.   A   185.199.108.153
   apphive.co.in.   A   185.199.109.153
   apphive.co.in.   A   185.199.110.153
   apphive.co.in.   A   185.199.111.153
   ```
5. Wait 5–60 minutes for DNS + SSL certificate.
6. Verify:
   ```bash
   curl -I https://apphive.co.in
   curl https://apphive.co.in/ads.txt
   ```
7. Submit `apphive.co.in` to AdSense for review.

## After AdSense approval
1. Create Ad Units in the AdSense dashboard for inline placements.
2. Replace each empty `data-ad-slot=""` in `index.html` with the actual slot ID.
3. Push the changes.

Once approved at the apex, ads serve on every subdomain too — including `nz.apphive.co.in` (TrafficNZ).
