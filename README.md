# System Arise

365-day life reset challenge app. Solo Leveling style: daily quests, XP, levels, ranks, gym planner with auto kg progression, body tracking and achievements.

The whole app is one file: `index.html`. Data autosaves in the phone's browser and can sync to Firebase (⚙ Settings → Cloud sync).

## Folder structure

```
index.html              ← the app
manifest.webmanifest    ← makes it installable, opens full screen
sw.js                   ← offline support (works without internet)
icons/                  ← app icon
IMAGE-LIST.md           ← every image file name to create (checklist)
images/
  achievements/         ← 1080 × 1080  e.g. first.jpg, s7.jpg
  quests/               ← 1080 × 600   e.g. protein.jpg
  sessions/             ← 1080 × 600   e.g. chest-triceps.jpg, rest.jpg
  exercises/            ← 1080 × 600   e.g. bench-press.jpg
  poses/                ← 1080 × 1080  e.g. bench-press.jpg (1 image, all poses inside)
```

## Image rules

- Format: **.jpg** only.
- Names must match `IMAGE-LIST.md` exactly: small letters, words joined with `-`.
- Keep each image under ~300 KB (export at 80% quality).
- Missing images are fine. The app shows its built-in default.
- Images can only be added or changed here in the repo. The app has no upload or edit option.
- Which image the app shows, in order:
  1. Firebase `system/images` URL (if cloud sync is on)
  2. This repo's `images/` folder
  3. Built-in default

## Publish

### Option A: GitHub Pages (public repo)
1. Repo → Settings → Pages → Source: *Deploy from a branch* → Branch `main`, folder `/ (root)` → Save.
2. After 1–2 minutes the app is live at `https://<username>.github.io/<repo-name>/`.

### Option B: Vercel (works with a private repo)
1. vercel.com → Add New → Project → import this repo → Deploy (no settings needed).

### After publishing
- Open the link on the phone in Chrome → ⋮ → **Install app** (or **Add to Home screen**). Opened from the home screen icon, it runs full screen: no address bar, no tabs, no browser buttons.
- Firebase: Authentication → Settings → **Authorized domains** → add the GitHub Pages or Vercel domain.

## Updating

Edit or add files, commit, push. GitHub Pages and Vercel redeploy automatically. On the phone, close and reopen the app to load the new version. If you change `sw.js`, bump `CACHE = 'system-arise-v1'` to `v2`.

Data on the phone is **not** stored in the repo, so updating the app never deletes progress. Do not put any Firebase keys or personal data in this repo.
