# 🍽️ Lunch Sync

A dead-simple web app for two people working from home to share their lunch availability. Set your window, see your partner's — and find when you can eat together.

---

## Features

- **Real-time sync** — updates appear instantly on both devices
- **Overlap detection** — visual timeline shows when you can eat together
- **Mobile-first** — designed for quick phone use during the workday
- **Zero accounts** — just pick "Person 1" or "Person 2" on each device
- **Resets daily** — only shows today's availability

---

## Setup (5 minutes)

### 1. Create a Supabase project (free)

1. Go to [supabase.com](https://supabase.com) and sign up / log in
2. Click **New Project**
3. Name it anything (e.g. `lunch-sync`), set a database password, pick a region → **Create**
4. Wait ~30 seconds for the project to spin up

### 2. Create the database tables

1. In your Supabase dashboard sidebar, click **SQL Editor**
2. Click **New query**
3. Paste the entire contents of `setup.sql` from this repo
4. Click **Run** — you should see "Success" for each statement

### 3. Get your credentials

1. In the sidebar, click **Settings** (gear icon) → **API**
2. You need two values:
   - **Project URL** — shown under "Project URL" (looks like `https://abcdefg.supabase.co`)
   - **anon public key** — shown under "Project API keys" → the `anon` / `public` key (starts with `eyJ...`)

### 4. Paste your credentials into the app

Open `index.html` and find these lines near the top of the `<script>`:

```js
const SUPABASE_URL      = "YOUR_SUPABASE_URL";
const SUPABASE_ANON_KEY = "YOUR_SUPABASE_ANON_KEY";
```

Replace them with your real values:

```js
const SUPABASE_URL      = "https://abcdefg.supabase.co";
const SUPABASE_ANON_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...";
```

### 5. Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "lunch sync"
gh repo create lunch-sync --public --push
```

Then in your GitHub repo → **Settings** → **Pages** → Source: **Deploy from a branch** → `main` / `/ (root)` → **Save**.

Live at `https://YOUR_USERNAME.github.io/lunch-sync/` within a minute.

### 6. Use it

1. Open the URL on your phone → pick **Person 1**
2. Partner opens the same URL → picks **Person 2**
3. Each device remembers who you are

---

## How it works

- Single HTML file, no build step
- Supabase Realtime pushes changes instantly to the other device
- Data stored per-day (`lunch_date = "2026-06-27"`) so it auto-resets
- Each device stores its identity in `localStorage`

---

## Cost

Supabase free tier includes 500 MB database, 5 GB bandwidth, and unlimited API requests. A two-person lunch app will use approximately none of that.

---

## License

MIT
