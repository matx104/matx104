# 🔌 Live Widgets Setup — matx104/matx104

Everything here is **free**. Drop the `.github/workflows/*.yml` files into the
root of your `matx104/matx104` profile repo (keep the `.github/workflows/`
path exactly), then follow the per-widget steps below.

> One-time repo setting: **Settings → Actions → General → Workflow permissions
> → Read and write permissions** (lets Actions commit README updates).

---

## 1 · 📈 WakaTime — Weekly Dev Breakdown
Fills the `<!--START_SECTION:waka-->` block.

1. Sign up free at **wakatime.com**.
2. Install the **WakaTime** plugin in each editor you use (VS Code, JetBrains,
   Vim, etc.) and paste your key when prompted.
3. Copy your key from **wakatime.com → Settings → API Key**.
4. In the repo: **Settings → Secrets and variables → Actions → New repository
   secret** → name `WAKATIME_API_KEY`, value = your key.
5. Commit `.github/workflows/waka.yml`. Run it manually once from the **Actions**
   tab, then let it populate over a few days of coding.

Markers are already in your README — no edits needed. ✅

---

## 2 · 📝 Medium Blog Posts
Fills the `<!-- BLOG-POST-LIST:START -->` / `END` block.

1. No key required.
2. Commit `.github/workflows/blog.yml`.
3. Run it once from the **Actions** tab. It pulls
   `https://medium.com/feed/@matx104` every 6 hours and swaps in your latest posts.

> Note: the default action output is a link list. If you want to keep the exact
> table you have now, either accept the list format or tell me and I'll hand you
> a matching `template:` string.

---

## 3 · 🎵 Spotify Now-Playing (novatorem card)
Powers the `novatorem-matx104.vercel.app` image. Free via Spotify Developer +
Vercel Hobby. This one is a **deploy**, not a workflow.

### A. Create the Spotify app
1. Go to **developer.spotify.com/dashboard** → **Create app**.
2. Set **Redirect URI** to `http://localhost:3000/callback` (temporary, for the
   token grab).
3. Copy the **Client ID** and **Client Secret**.

### B. Get a refresh token (one-time)
1. Open this URL in a browser (replace `CLIENT_ID`):
   ```
   https://accounts.spotify.com/authorize?client_id=CLIENT_ID&response_type=code&redirect_uri=http://localhost:3000/callback&scope=user-read-currently-playing%20user-read-recently-played
   ```
2. Approve. You'll be bounced to `localhost:3000/callback?code=XXXX` (page won't
   load — that's fine). **Copy the `code` value** from the URL.
3. Exchange the code for tokens. Run this (fill in the 3 values):
   ```bash
   curl -X POST https://accounts.spotify.com/api/token \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d grant_type=authorization_code \
     -d code=THE_CODE_FROM_STEP_2 \
     -d redirect_uri=http://localhost:3000/callback \
     -u CLIENT_ID:CLIENT_SECRET
   ```
4. From the JSON response, copy **`refresh_token`** (it's long-lived).

### C. Deploy the card (Vercel free)
1. Fork **`natemoo-re/spotify-github-profile`** *or* **`kittinan/spotify-github-profile`**
   (both free & maintained). *(Your current card uses a novatorem-style deploy —
   any of these works; the embed URL just needs to resolve.)*
2. Import the fork into **vercel.com** (Hobby tier, free).
3. Add these **Environment Variables** in Vercel:
   | Key | Value |
   |---|---|
   | `SPOTIFY_CLIENT_ID` | from A |
   | `SPOTIFY_CLIENT_SECRET` | from A |
   | `SPOTIFY_REFRESH_TOKEN` | from B4 |
4. Deploy. Vercel gives you a URL like `your-project.vercel.app`.
5. Point the README `<img>` at that deployment's spotify endpoint (your current
   embed already follows this shape — just match the new host if it changed).

Play a track → refresh your profile → it goes live. 🎧

---

## 4 · 🐍 Contribution Snake (already wired)
Your README already reads the SVGs from the `output` branch. `snake.yml` keeps
them fresh — commit it and run once. No secrets; it uses the built-in
`GITHUB_TOKEN`.

---

## ✅ Quick checklist
- [ ] Workflow permissions set to **Read and write**
- [ ] `WAKATIME_API_KEY` secret added
- [ ] All 3 workflows committed under `.github/workflows/`
- [ ] Each workflow run once from the **Actions** tab
- [ ] Spotify app + refresh token + Vercel deploy done
