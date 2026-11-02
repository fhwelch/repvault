# RepVault v1: GitHub Pages edition

A no-build mobile-first workout tracking PWA with two **local** profile selectors, a preloaded searchable exercise library, shared workout templates, set logging, history, and JSON backup export.

## Publish using GitHub Pages

1. Create a new **public** repository on GitHub, for example `repvault`. Do not add a starter README or license.
2. Unzip this archive. Upload **all files and the `.github` folder inside `repvault`** to the **root** of the new repository, not a nested `repvault/` folder. GitHub's web uploader may hide dotfolders on some systems; using Git locally is more reliable (see below).
3. In GitHub open **Settings → Pages → Build and deployment → Source** and select **GitHub Actions**.
4. Commit/push to the `main` branch. Open **Actions** and wait for `Deploy RepVault to GitHub Pages` to finish.
5. Visit `https://YOUR-USERNAME.github.io/repvault/` (replace username and repository name with yours; the exact URL appears under Settings → Pages).
6. On iPhone Safari, open the site and choose **Share → Add to Home Screen**. Test exercise search and save a practice workout.

### Git command-line option

From the unzipped `repvault` directory:

```sh
git init
git add .
git commit -m "Initial RepVault PWA"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/repvault.git
git push -u origin main
```

Create the empty repository in GitHub first. Git authentication may require GitHub CLI or a credential manager.

## Local development

```sh
python3 -m http.server 8080
```

Open `http://localhost:8080`.

## Data & privacy limitations

- **Important:** Both profile options are local labels, not logins. Data stays in each browser's `localStorage`; it is **not synchronized** between devices.
- GitHub Pages hosts **public static application code**. Do not commit private workout records, personal data, passwords, or Supabase service-role keys.
- Use **History → Export JSON** to save regular backups. Browser storage can be cleared and is not a durable shared database.
- The app caches its static files for offline use, but offline support should be tested on each target device.

## Supabase phase (not connected yet)

`supabase/schema.sql` is an **initial planning schema**, not a deployed backend. It enables RLS with no policies, so client access is denied until proper household membership/invitation policies are implemented and tested. Next steps: create Supabase project, add email authentication, implement household invitation flow and membership-secured RLS, integrate Supabase JS into the UI, and migrate local data carefully after account login. Never place a service-role key in the frontend.
