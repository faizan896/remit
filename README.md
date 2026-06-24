# remit — remittance fee comparator

A single-page web app that shows how much money **actually arrives** when sending abroad — exposing the hidden exchange-rate margin, not just the upfront fee.

## Files
- `index.html` — the entire app (HTML + CSS + JS in one file, no backend).

## Run locally
Just double-click `index.html`, or open it in any browser.

## Deploy to Netlify (free)
1. Go to https://app.netlify.com → **Add new site → Deploy manually**.
2. Drag this whole **remit** folder onto the upload area.
3. Netlify gives you a live URL in seconds.

(Optional: rename your site under Site settings → Domain management.)

## How it works
- Fetches the live mid-market rate from `https://open.er-api.com/v6/latest/{FROM}` (no API key).
- For each provider: `fee` (flat or % of send), `providerRate = mid * (1 - margin%)`, `received = (amount - fee) * providerRate`, `lostVsReal = amount*mid - received`.
- Ranks providers by amount received (highest = best). Best is green, worst is red.

Provider fees/margins are approximate — verify with each provider before sending.
