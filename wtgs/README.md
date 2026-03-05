# Author Website

Personal website for book promotion, workshop bookings, and author information.

## File Structure

```
author-website/
├── index.html          ← Public website (visitors see this)
├── admin.html          ← Admin panel (password protected)
├── README.md           ← This file
└── content/            ← All your website content as JSON
    ├── site.json       ← Site name, SEO title, theme selection
    ├── hero.json       ← Hero headline, subtitle, buttons, book cover URL
    ├── about.json      ← Author bio, photo URL, pull quote
    ├── book.json       ← Book feature cards
    ├── stores.json     ← Purchase links (Amazon, Flipkart, etc.)
    ├── events.json     ← Workshops and webinars
    ├── faq.json        ← FAQ accordion items
    └── contact.json    ← Location, social links, footer text
```

## What goes WHERE

| File | Goes to | Notes |
|------|---------|-------|
| `index.html` | This GitHub repo | The public website |
| `admin.html` | This GitHub repo | Admin panel |
| `content/*.json` | This GitHub repo | All content — edited via admin panel |
| `worker.js` | Cloudflare Worker (NOT here) | Privacy proxy — contains references to secrets |

## ⚠️ What NOT to put in this repo

Never add these to GitHub:
- Your email address
- Your phone number  
- Bank account details
- UPI ID
- Admin password
- GitHub Personal Access Token

All of the above live in **Cloudflare Worker → Settings → Variables** as encrypted secrets.

## Hosting

- **Website**: Cloudflare Pages (connected to this repo — auto-deploys on every push)
- **Images**: Cloudflare R2 (URLs stored in the JSON files above)
- **Privacy proxy**: Cloudflare Worker (separate — see `worker.js` in your downloads)
- **Domain**: Configured in Cloudflare

## Making content changes

Use the admin panel at `yourdomain.in/admin.html`.  
Changes save back to this repo automatically via the Cloudflare Worker.  
The site rebuilds within 30–60 seconds of saving.
