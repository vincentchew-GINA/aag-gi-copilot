# AAG GI Co-Pilot — Vercel Deployment Guide

## What's in this folder

```
gi-copilot/
├── api/
│   └── chat.js          ← Serverless proxy (keeps API key secret)
├── public/
│   └── index.html       ← Full Co-Pilot frontend
├── vercel.json          ← Routing config
├── package.json
└── README.md
```

## Deploy in 5 steps

### Step 1 — Create a free Vercel account
Go to https://vercel.com and sign up (free tier is sufficient).

### Step 2 — Install Vercel CLI
```bash
npm install -g vercel
```

### Step 3 — Deploy
Open Terminal, navigate to this folder, and run:
```bash
cd gi-copilot
vercel
```
Follow the prompts — accept all defaults.

### Step 4 — Add your Anthropic API key
In the Vercel dashboard:
1. Go to your project → Settings → Environment Variables
2. Add: Name = `ANTHROPIC_API_KEY`, Value = your key from https://console.anthropic.com
3. Redeploy: `vercel --prod`

### Step 5 — Done
Vercel gives you a URL like `https://aag-gi-copilot.vercel.app`
Share that link with any FC — it works on desktop and mobile.

## Updating the knowledge base
Edit `public/index.html` — find the `SYS` variable (the system prompt).
Add new product knowledge, insurer-specific details, or premium tables there.
Run `vercel --prod` to redeploy.

## Updating the GINA Portal link
In `public/index.html`, search for `window.open('#'` and replace `#` with your actual GINA Portal URL.

## Cost
- Vercel: Free tier handles ~100,000 requests/month — more than enough for FC use
- Anthropic API: ~SGD 0.01–0.03 per conversation (claude-sonnet-4)
