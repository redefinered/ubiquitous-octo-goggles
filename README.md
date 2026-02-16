# ParkU Info & Support

Static site for **parku.info**: info and support content for the ParkU app (e.g. account deletion for Google Play).

- **Live:** https://parku.info (after DNS and first deploy)
- **Delete account (Play Store URL):** https://parku.info/delete-account.html

## Deploy (GitHub Pages)

1. **Create the GitHub repo** (e.g. `parku-info`) and push this code:
   ```bash
   git remote add origin git@github.com:YOUR_USERNAME/parku-info.git
   git push -u origin main
   ```

2. **Use GitHub Actions for Pages**
   - Repo → **Settings** → **Pages**
   - Under **Build and deployment**, set **Source** to **GitHub Actions** (not “Deploy from a branch”).

3. **Custom domain parku.info**
   - In **Settings** → **Pages**, under **Custom domain**, enter `parku.info`
   - Click **Save**. GitHub will show the DNS records to add.
   - **Enforce HTTPS** (recommended) once DNS has propagated.

4. **DNS at your registrar**
   - For **apex** (parku.info):
     - Add **A** records pointing to:
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`
   - Or use a **CNAME** for `www` only: `www` → `YOUR_USERNAME.github.io` (and optionally redirect apex to www).

   [GitHub docs: Custom domain for GitHub Pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

After the first push to `main`, the workflow deploys the `public/` folder to GitHub Pages. The `CNAME` file in `public/` tells Pages to serve the site at **parku.info**.

## Local preview

Serve the `public/` folder with any static server, e.g.:

```bash
cd public && npx serve .
# or: python3 -m http.server 8000
```

Then open http://localhost:3000 (or the port shown).

## Structure

- `public/` – static site (deployed as-is)
  - `index.html` – info/support landing
  - `delete-account.html` – account & data deletion (Play Store “Delete account URL”)
  - `styles.css` – shared styles
  - `CNAME` – custom domain (parku.info)
