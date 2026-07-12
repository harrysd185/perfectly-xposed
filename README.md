# Perfectly Xposed — self-service photo editor setup

This turns your site into one you can update yourself: go to
`perfectlyxposed.com/admin`, log in, add a photo, publish. No code, no scripts.

You only do this setup **once**. After that, adding photos takes about a minute.
Do the steps in order — I'll walk you through each one in chat.

---

## What's in this folder
- `index.html` — your site (gallery now loads from `data/gallery.json`)
- `data/gallery.json` — the list of gallery photos (the editor writes to this)
- `admin/` — the editor (`/admin` on your site) and its `config.yml`
- `images/uploads/` — where photos you upload get saved
- `netlify.toml` — tells Netlify to serve the site as-is (no build step)

---

## Step 1 — Put this on GitHub
1. On GitHub, create a new repository named **`perfectly-xposed`**.
2. Upload everything in this folder into that repo (you can drag the files and
   folders straight into GitHub's "Add file → Upload files" page).

## Step 2 — Connect the repo to your existing Netlify site
This keeps your domain and just changes where deploys come from (Git instead of
drag-and-drop), so `perfectlyxposed.com` keeps working.
1. In Netlify, open your **amazing-fairy-906d20** site.
2. Site configuration → Build & deploy → Continuous deployment → **Link repository**.
3. Pick your `perfectly-xposed` repo. Leave build command empty; publish directory `.`.

## Step 3 — Set up the login (DecapBridge)
The old built-in login (Netlify Identity) is deprecated, so we use DecapBridge —
a free service made specifically for this.
1. Go to **decapbridge.com** and sign in with GitHub.
2. Add a site and select your `perfectly-xposed` repo.
3. It gives you two values — your **repo** and an **identity_url (site id)**.
4. Open `admin/config.yml`, fill in the three `>>> FILL IN <<<` lines, and save/commit.
5. Create your editor login (email + password) in DecapBridge.

## Step 4 — Use it
1. Go to **perfectlyxposed.com/admin** and log in.
2. Click **Gallery → Gallery photos**, then **Add photo**: drag in an image,
   type a title + location, pick a category, and **Publish**.
3. Netlify redeploys automatically. Your new photo is live in ~1 minute.

---

### Tips
- Replacing the samples: delete the placeholder entries in the editor as you add
  your own. (They're the picsum.photos images.)
- Big camera files are fine, but resizing to ~2000px wide keeps the site fast.
- The "Featured" banner image near the top is still set in `index.html` directly;
  ask me if you want that made editable too.
