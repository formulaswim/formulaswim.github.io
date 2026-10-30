# Formula Swim website

Static support site and privacy policy for the Formula Swim iPhone game. Plain HTML + CSS, no JavaScript, no trackers.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Home + support page (pitch, FAQ, contact). Use as **Support URL** and **Marketing URL**. |
| `privacy.html` | Privacy Policy. Use as **Privacy Policy URL** in App Store Connect. |
| `style.css` | Shared stylesheet (dark, racing-red accent, mobile-friendly). |
| `app-ads.txt` | AdMob authorized-seller file. Must be served from the root of the domain. |
| `.nojekyll` | Tells GitHub Pages to serve files as-is. |

## Before publishing: replace the email placeholder

Search for `SUPPORT_EMAIL_HERE` and replace it with your support email:

```sh
grep -rn SUPPORT_EMAIL_HERE .
sed -i '' 's/SUPPORT_EMAIL_HERE/you@example.com/g' index.html privacy.html
```

## Publish with GitHub Pages (free)

1. Create a GitHub account if you don't have one.
2. Create a new **public** repository. Two options:
   - **Recommended:** name it `<your-username>.github.io`. The site is then at `https://<your-username>.github.io/`, which is the *root* of the domain, so `app-ads.txt` works.
   - Any other name (e.g. `formula-swim`) puts the site at `https://<your-username>.github.io/formula-swim/`. That is **not** the domain root, so AdMob can't find `app-ads.txt` there unless you use a custom domain (see below).
3. Upload the files from this folder to the repository root (drag them into "Add file → Upload files" on github.com, or use git):
   ```sh
   cd ~/Developer/"Formula Swim Site"
   git init && git add . && git commit -m "Formula Swim site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo>.git
   git push -u origin main
   ```
4. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
5. After a minute or two, check:
   - `https://<your-site>/`
   - `https://<your-site>/privacy.html`
   - `https://<your-site>/app-ads.txt`

### Custom domain (optional)

If you buy a domain (e.g. `formulaswim.com`), add it under Settings → Pages → Custom domain and follow GitHub's DNS instructions. Then `app-ads.txt` lives at `https://formulaswim.com/app-ads.txt`.

## App Store Connect

- **Support URL:** `https://<your-site>/`
- **Marketing URL:** `https://<your-site>/`
- **Privacy Policy URL:** `https://<your-site>/privacy.html`

### Important: app-ads.txt

`app-ads.txt` must sit at the **root of the domain** used as the **Marketing URL** (or developer website) in App Store Connect. AdMob reads the domain from your App Store listing and looks for `https://<that-domain>/app-ads.txt`; a file in a subfolder is ignored. After the app is live, AdMob verifies it within about 24 hours (AdMob → Apps → View all apps → app-ads.txt tab).

Contents:

```
google.com, pub-2004304658966176, DIRECT, f08c47fec0942fa0
```
