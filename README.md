# Native Ad Studio

An internal tool for Decide.co's creative team to develop native ad content packages end-to-end — from campaign brief to DollarBird-ready creative brief.

**Live site:** https://florayu37.github.io/native-ad-studio/

---

## What it does

**Step 1 — Campaign Brief**
Fill in offer details, target audience, landing page, and angle/key message. Optionally generate angle suggestions pulled from live Google Search Trends across T14 markets (US, UK, CA, AU, NZ, IE, ZA, IN, PH, SG, NG, GH, MY, HK).

**Step 2 — Headlines**
- Paste client-provided Traffic Unit and Poll Style headlines
- AI-generate 20 traffic headlines + 15 poll headlines + 1 universal description
- Select your launch package (bolded in the final brief)

**Step 3 — Images**
- Upload raw images; the tool crops and resizes to 1600×900
- Optional play button overlay variants (NPB / PB naming convention)
- Auto-renames files: `OfferName_YYYY-MM-DD_NPB-01.jpg` / `_PB-01.jpg`
- Download all as ZIP or upload directly to Google Drive

**Step 4 — Brief**
- AI-generates cover image titles (vision model reads each image)
- Outputs a complete DollarBird creative brief
- Copy to clipboard pastes rich HTML into Asana with correct bold formatting

---

## Setup

Open the tool and click the ⚙ Settings icon (top right) to enter:

| Key | Where to get it |
|-----|----------------|
| Anthropic API Key | [console.anthropic.com](https://console.anthropic.com) |
| SerpAPI Key *(optional, for Trends)* | [serpapi.com](https://serpapi.com) |
| Google OAuth Client ID *(optional, for Drive upload)* | Google Cloud Console → APIs & Services → Credentials |

Keys are stored in `localStorage` — never sent anywhere except the respective APIs.

---

## Stack

Single-file React 18 app (no build step). All processing is client-side.

- React 18 + Babel standalone
- Tailwind CSS (CDN)
- Anthropic API (`claude-sonnet-5` for copy, `claude-haiku-4-5-20251001` for vision)
- SerpAPI Google Trends
- smartcrop.js · gifuct-js · gif.js · JSZip
- Google Identity Services (OAuth for Drive)
