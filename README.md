# GoldenHour — Chase the Light

**Live:** https://abhiramunni.github.io/goldenhour/

The best light of the day, planned before it happens. GoldenHour works out golden hour, blue hour, sunrise and sunset for your city — on your device, with no account and no tracking — and helps you plan the shots before the light runs out.

## What it does

- **The light, right now** — a live card that names the current window (golden hour, blue hour, daylight or night), counts down to the next change second by second, and explains in plain words what the light is good for.
- **The sun's path, drawn out** — an SVG arc of today's sun with the golden windows highlighted, plus sunrise, sunset and solar noon.
- **Seven days of light** — golden-hour windows for the next 7 days, with cloud cover at evening golden hour from Open-Meteo (free, no key). The clearest evening gets a "Best light" badge. If the forecast is offline, the sun times still work.
- **Your shot list** — plan each shot with the window it needs (morning golden, evening golden, blue hour, anytime), tick shots off as you take them, and see your progress. Seeded with 4 sample shots you can remove in one tap.
- **Camera settings, plain and simple** — starting points for 6 scenes (golden-hour portrait, blue-hour city, car at dusk, night street, bright midday, monsoon/overcast) with aperture, ISO, shutter and one plain-language tip each. The same numbers apply in a phone's Pro / Manual mode.
- **Five things worth knowing** — short plain-language guides, including why golden hour is short near the equator (under 35 minutes in Bengaluru and Kozhikode in November).
- **8 Indian cities + your own place** — Bengaluru, Kozhikode, Kochi, New Delhi, Mumbai, Chennai, Hyderabad, Kolkata, or add any place by latitude/longitude (plus an optional "use my location" button).
- **Copy today's plan** — one tap copies the day's windows and shot list as plain text.

## How the sun times are calculated

On-device, using the standard NOAA solar calculation (Julian day → solar declination and equation of time → hour angle for a given solar altitude). Golden hour means the sun 0–6° above the horizon; blue hour means the sun up to 6° below it. Indian cities use IST (UTC +5:30); a custom place outside India follows the device's timezone. Times are a guide — hills, buildings and weather shift the real light by a few minutes.

Hand-checked for Bengaluru, 17 Nov 2026: sunrise 6:19 AM, sunset 5:50 PM, solar noon 12:04 PM, golden hour 6:19–6:49 AM and 5:20–5:50 PM, noon sun elevation 58.1°.

## Tech

- One single self-contained `index.html` — no backend, no build step, no signup.
- Data is saved only in the browser's localStorage (city, shots, tour/intro state).
- Two AI-generated warm-editorial photos embedded as base64 (golden-hour car on a coastal road; camera flat-lay).
- Fonts: Fraunces + Inter (Google Fonts). Cloud cover: Open-Meteo forecast API, fetched with a 6-second timeout and an offline fallback.
- QA: 73/73 headless jsdom assertions (solar math cross-checked against known values, city comparisons, light classification, shot-list CRUD, samples/erase flow, intro + coach flow, copy summary, custom place), `node --check` clean, zero uncaught JS errors.

## Privacy

No account, no analytics, no tracking. Nothing leaves the device except the optional Open-Meteo cloud-cover request (latitude/longitude only, no identity).
