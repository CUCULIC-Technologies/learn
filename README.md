# learn

A central repo for self-paced learning pages, field guides, and reference material. Built as static HTML and deployed to Vercel.

## Structure

```
learn/
├── index.html              # Landing page that links to all resources
├── pages/                  # Individual learning pages
│   └── claude-toolbox.html
├── vercel.json             # Vercel config (clean URLs)
├── .gitignore
└── README.md
```

## Adding a new learning page

1. Drop the HTML file into `pages/` (e.g. `pages/react-basics.html`).
2. Open `index.html` and add a new `<li class="resource-card">` block in the `<ul class="resource-list">`, pointing to the new page.
3. Commit and push — Vercel auto-deploys on push to `main`.

## First-time setup

### 1. Create the GitHub repo

```bash
cd learn
git init
git add .
git commit -m "Initial commit: learn repo scaffold"
git branch -M main
```

Then on GitHub, create a new empty repo called `learn` (personal account, no README/license — keep it empty so the push works clean), and:

```bash
git remote add origin https://github.com/<your-username>/learn.git
git push -u origin main
```

### 2. Wire up Vercel

1. Go to [vercel.com](https://vercel.com) and sign in with GitHub.
2. Click **Add New → Project**.
3. Import the `learn` repo.
4. Framework preset: **Other** (Vercel auto-detects this as a static site).
5. Leave build command empty, output directory empty.
6. Click **Deploy**.

You'll get a `learn-<hash>.vercel.app` URL immediately.

### 3. Custom domain (`learn.yourdomain.com`)

1. In the Vercel project, go to **Settings → Domains**.
2. Add `learn.yourdomain.com`.
3. Vercel will show you the DNS record to create. Two options:
   - **CNAME** (typical): point `learn` → `cname.vercel-dns.com` at your DNS provider.
   - **A record**: point `learn` → `76.76.21.21`.
4. Save the DNS record. Propagation usually takes a few minutes to an hour.
5. Vercel automatically provisions a TLS cert once DNS resolves.

### 4. Subsequent deploys

```bash
git add .
git commit -m "Add <page>"
git push
```

Vercel picks it up and deploys in ~10 seconds.

## Local preview

Any static file server works. Quickest option:

```bash
npx serve .
```

Or with Python:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
