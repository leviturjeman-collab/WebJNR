# JNR Transfers — Setup Guide

## What's Included

Single-file premium website (`index.html`) with:

- **Three.js** animated gold particle background with interactive torus wireframe
- **Google Places Autocomplete** on pickup/dropoff fields (auto + manual mode toggle)
- **Full booking form**: one-way, round trip, by-the-hour tabs
- **Passenger counters**, suitcase counters, child seat selector, extra items (stroller, wheelchair, golf, ski, surfboard, pet)
- **Flight/train number**, vehicle type, meet & greet name board
- **Contact details** with preferred method (WhatsApp, call, email, SMS)
- **Fleet section**, services grid, stats bar, contact cards
- **WhatsApp floating button** (FAB)
- **Success modal** on form submission
- **Fully responsive** (mobile-first)
- Black & gold luxury aesthetic with Cormorant Garamond + Outfit typography

## Before Going Live — Required Steps

### 1. Google Maps API Key

Replace `YOUR_API_KEY` in the `<script>` tag near the top of the file:

```
script.src = 'https://maps.googleapis.com/maps/api/js?key=YOUR_ACTUAL_KEY&libraries=places&callback=initAutocomplete';
```

Enable these APIs in Google Cloud Console:
- Maps JavaScript API
- Places API

Restrict key to your domain for security.

### 2. Phone Numbers & Email

Search and replace all instances of:
- `+34 600 000 000` → your real number
- `34600000000` → your real number (no spaces, for WhatsApp links)
- `info@jnrtransfers.com` → your real email

### 3. Form Submission Backend

The form currently logs data to `console.log`. Connect it to one of:

- **EmailJS** (free tier: 200 emails/month) — add their SDK and send email on submit
- **Formspree** — change the form action to your Formspree endpoint
- **Custom API** — POST the `data` object to your backend
- **WhatsApp redirect** — format data into a WhatsApp message URL

Look for the `// TODO` comment in `handleSubmit()`.

### 4. Stats & Content

Update the placeholder stats (10K+, 4.9 rating, etc.) and fleet details with your real data.

### 5. Hosting

Upload `index.html` to any static host: Vercel, Netlify, Cloudflare Pages, or traditional hosting. No build step needed — it's a single file.

## Address Autocomplete Behavior

- Fields default to **Google Places Autocomplete** (restricted to Spain)
- Users can click **"Manual"** to switch to free-text entry
- If Google Maps fails to load (no API key), fields still work as plain text inputs
- Autocomplete returns establishment names + formatted addresses
