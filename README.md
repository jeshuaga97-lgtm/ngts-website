# NextG Tile Solutions (NGTS) — Production Website

This folder is the complete, self-contained production build of the NGTS homepage. It is a single `index.html` file — all images are embedded directly in the file (as base64 data), so there are no separate image files, no build step, and no dependencies to install.

## Deploying to Vercel

**Option A — Drag and drop (fastest, no account setup beyond signing in):**
1. Go to https://vercel.com/new
2. Drag this whole folder (or just `index.html`) onto the upload area
3. Vercel will detect it as a static site automatically — no framework, no build command needed
4. Click Deploy

**Option B — Vercel CLI:**
```
npm install -g vercel
cd ngts-website-production
vercel --prod
```

**Option C — GitHub:**
1. Push this folder to a GitHub repository
2. Import the repo at https://vercel.com/new
3. Leave the framework preset as "Other" / static — no build command, no output directory override needed
4. Deploy

Once deployed, Vercel will give you a live URL, and you can attach your own domain (e.g. nextgtilesolutions.com) from the project's Domains settings.

## What's inside `index.html`

- Full homepage markup, all CSS, and all JavaScript in one file
- All photography and the NGTS logo embedded directly as base64 image data — nothing loads from an external image host, so nothing can go missing or 404
- One external dependency: Google Fonts (Bricolage Grotesque + Inter), loaded from `fonts.googleapis.com` / `fonts.gstatic.com`. This is standard and will load normally on any real hosting with internet access.

## Contact form — one-time setup step

The "Submit Request" form delivers submissions to **Jeshua@nextgtilesolutions.com** via FormSubmit.co, a free email-delivery service for static sites. No API key or account was needed to wire this up.

**The first time the form is ever submitted for real** (after this goes live), FormSubmit will send one confirmation email to Jeshua@nextgtilesolutions.com. Click the confirmation link in that email once — after that, every submission (from that point forward, permanently) delivers straight to the inbox automatically, with no further action needed.

Recommended: right after deploying, submit one test entry through the live form yourself so you're the one who receives and clicks that one confirmation email, rather than a real customer.

Note: the free tier of this integration delivers all typed form fields (name, phone, email, project type, location, description) but does not attach uploaded photo files to the email — the notification just tells you how many photos the customer selected, so you know to follow up with them directly. If you want photos automatically attached to the email itself, that requires upgrading to a paid tier of a form-delivery service (e.g. Web3Forms Pro) — let me know if you'd like that wired up instead.

## Notes on this build

- Fully responsive: desktop, tablet, and mobile layouts, including a mobile hamburger menu
- The `<meta name="viewport">` tag is required for the mobile layout to render correctly on real phones — it's included in this file. (This tag is automatically added by Claude's own preview tool, so it wasn't visible as missing until this production file was assembled — it's in place here.)
- "Email Us Directly" opens the visitor's default email app via a `mailto:` link to Jeshua@nextgtilesolutions.com
- No tracking scripts, analytics, or third-party code beyond the Google Fonts stylesheet and the FormSubmit.co form endpoint
