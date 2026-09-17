# Strategy Stats Tracker

A installable PWA for tracking R-multiple milestones (1.5R / 2R / 3R), breakeven-after-2R retests,
total R, expectancy, and max drawdown — with GitHub-backed storage for your trade data.

## Files

```
index.html          the app
manifest.json        PWA manifest (name, icons, colors)
service-worker.js    offline caching for the app shell
icons/icon-192.png
icons/icon-512.png
```

## Deploy on GitHub Pages

1. Create a new GitHub repo (public or private) and upload all these files to the root
   (keep the `icons/` folder structure intact).
2. In the repo, go to **Settings → Pages**.
3. Under "Build and deployment", set **Source** to "Deploy from a branch", pick your
   default branch (e.g. `main`) and folder `/ (root)`, then save.
4. GitHub will give you a URL like `https://<username>.github.io/<repo>/`. It can take
   a minute to go live.

PWAs require HTTPS to install — GitHub Pages serves over HTTPS by default, so no extra setup needed.

## Install as an app

**On iPhone/iPad (Safari):** open the GitHub Pages URL → Share button → "Add to Home Screen".

**On Android (Chrome):** open the URL → menu (⋮) → "Install app" (or you'll see an automatic
install banner).

**On desktop (Chrome/Edge):** open the URL → click the install icon in the address bar
(or menu → "Install Strategy Stats Tracker...").

Once installed, it opens in its own window/icon like a native app and works offline for the
interface itself (your trade data still needs a connection to sync to/from GitHub).

## Storing your trade data

This app doesn't need its own backend — it saves your trade log straight to a GitHub repo
file via the GitHub Contents API. In the app, tap the ⚙ icon and fill in:

- **Repo owner** — your GitHub username
- **Repo name** — a repo you want the data saved into (can be the same repo you deployed
  the app to, or a separate private one — a separate private repo is recommended since your
  Personal Access Token will be entered here)
- **File path** — e.g. `strategy-stats.json`
- **Branch** — e.g. `main`
- **Personal Access Token** — a GitHub token with `repo` (or fine-grained "Contents:
  Read and write") permission on that repo

Then use **Load from GitHub** / **Save to GitHub** inside the app. Your data is also cached
locally in the browser so you don't lose anything between syncs.

> Note: the token is stored in your browser's local storage on whichever device you use the
> app on, not synced anywhere. Use a fine-grained token scoped only to the data repo.
