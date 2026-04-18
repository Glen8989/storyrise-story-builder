# Storyrise Story Builder — Deployment Guide

## What this is
A hosted web app that lets anyone with the link try the Storyrise Story Builder
and generate a complete personalised children's story. Your API key is stored
securely in Vercel and is never visible to users.

---

## Step 1 — Install the Vercel CLI

Open Terminal (Mac) or Command Prompt (Windows) and run:

    npm install -g vercel

If you don't have Node.js installed, download it first from https://nodejs.org

---

## Step 2 — Log in to Vercel

    vercel login

This opens a browser window. Sign up for a free Vercel account at vercel.com
if you don't have one, then approve the login.

---

## Step 3 — Deploy the app

Navigate to the storyrise-app folder:

    cd storyrise-app

Then run:

    vercel

Answer the prompts like this:
  - Set up and deploy? → Y
  - Which scope? → your account name
  - Link to existing project? → N
  - Project name? → storyrise-story-builder (or anything you like)
  - In which directory is your code located? → ./ (just press Enter)
  - Want to override settings? → N

Vercel will deploy and give you a URL like:
  https://storyrise-story-builder.vercel.app

---

## Step 4 — Add your API key (IMPORTANT)

Your API key must be added as a secure environment variable.
It is NEVER put in the code.

1. Go to https://vercel.com and open your project dashboard
2. Click Settings → Environment Variables
3. Click Add New
4. Name:  ANTHROPIC_API_KEY
5. Value: paste your Anthropic API key here
6. Environment: tick Production, Preview, and Development
7. Click Save

---

## Step 5 — Redeploy with the key active

Back in Terminal, run:

    vercel --prod

This deploys your final live version with the API key active.

---

## Step 6 — Share your URL

Your app is now live at the URL Vercel gave you. Share it with anyone
you want to trial the Story Builder. They don't need an account —
they just open the link and start building.

---

## Spending controls (recommended)

Set a monthly spending limit so there are no surprise charges:
1. Anthropic Console → Settings → Billing → Usage Limits
2. Set a monthly cap (e.g. $20 AUD)
3. The API will stop accepting requests if the cap is hit

Rough cost guide:
  1 story ≈ $0.02–0.05 AUD
  100 stories ≈ $2–5 AUD
  500 stories ≈ $10–25 AUD

---

## To update the app in future

Make changes to the files, then run:

    vercel --prod

That's it — the live URL stays the same, content updates instantly.

---

## Files in this project

  public/index.html   The Story Builder frontend (what users see)
  api/generate.js     The secure backend (handles API calls, hides your key)
  vercel.json         Routing config
  package.json        Project config

---

Questions? The Vercel free tier covers everything needed for a trial.
No credit card required for Vercel — only for Anthropic API usage.
