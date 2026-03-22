# CLAUDE.md — LED / WLED Setup Guide & PWA Controller

## Project Overview
Standalone HTML walkthrough guide for Bassahaulic customers setting up WLED on Gledopto GL-C-016WL-D controllers with WS2811 LED strips. Includes a Progressive Web App (PWA) for direct WLED controller management from mobile devices.

## Tech Stack
- **Setup Guide**: `index.html` (self-contained HTML + CSS + JS)
- **PWA Controller**: `app/index.html` + `app/sw.js` + `app/manifest.json`
- **Fonts**: Google Fonts — Audiowide (brand/primary headings), Orbitron (secondary headings/labels), Roboto (body)
- **No frameworks**, no build tools, no npm — static HTML files

## Design System (Bassahaulic Brand Theme)

### Colors
- Background: `#000000`
- Accent blue: `#0097ff`
- Blue: `#0097ff`
- Green: `#00ff66`
- Red: `#ff3333`
- Text: `#ffffff`
- Muted: `#cccccc`
- Borders: `rgba(255, 255, 255, 0.12)`

### Typography
- **Audiowide** — brand/primary headings, uppercase, letter-spacing 2-3px, weight 400
- **Orbitron** — secondary headings, labels, UI elements, uppercase, letter-spacing 1-2px, weight 700-900
- **Roboto** — body text, descriptions, weight 300-500

### Visual Effects
- **Matrix rain** — animated falling character canvas used as background effect (green/blue characters)
- **Glassmorphism** — frosted glass panels using `backdrop-filter: blur()` with semi-transparent backgrounds (`rgba(0, 0, 0, 0.6)` to `rgba(0, 0, 0, 0.85)`)
- Border radius: 12px (cards), 18px (large cards), 999px (pills)

## File Structure
```
LED/
├── index.html          # Complete setup walkthrough page
├── CLAUDE.md           # This file
├── README.md           # Project readme & TODO tracker
└── app/                # PWA — Bassahaulic WLED Controller
    ├── index.html      # PWA main interface (self-contained HTML + CSS + JS)
    ├── manifest.json   # PWA manifest (name, icons, theme color)
    ├── sw.js           # Service worker for offline caching
    └── icons/          # PWA icons (192x192, 512x512)
```

## Key Conventions

### Setup Guide (`index.html`)
- All CSS is embedded in `<style>` within `index.html` — no external stylesheets
- All JS is embedded in `<script>` at bottom of `index.html`
- Image placeholders use class `.img-placeholder` with dashed accent (blue) borders
- Copy-to-clipboard elements use `.code-val[data-copy]` attribute pattern
- Collapsible bonus sections use native `<details>/<summary>` elements
- Progress tracking uses IntersectionObserver on elements with IDs matching `data-target` attributes on `.progress-dot` buttons
- Step cards use `.step-card` with modifier classes: `--bonus`, `--trouble`, `--specs`
- Section color-coding: blue (accent) = main steps, blue = bonus, red = troubleshooting, green = specs

### PWA Controller (`app/`)
- Self-contained single-page app with embedded CSS and JS
- Connects to WLED devices over local network via JSON API and WebSocket
- Matrix rain canvas as animated background
- Glassmorphism panels for all UI surfaces
- Installable as PWA on iOS and Android (add to home screen)
- Service worker caches all assets for offline shell (still needs network for WLED communication)
- Network scan discovers WLED devices on the local subnet

## Hardware Reference (Gledopto GL-C-016WL-D)
- Input: DC 5/12/24V | Max 15A total, 10A per channel
- Default output: GPIO16 | Secondary: GPIO2
- Extended GPIOs: 18, 19, 25, 33
- Mic I2S pins: SD=26, WS=5, SCK=21
- Relay: GPIO 12
- WLED-AP password: `wled1234` | Config IP: `4.3.2.1`
- WS2811 color order: RGB

## WLED API Reference
- **JSON API**: `http://<device-ip>/json/state` — GET current state, POST to update (brightness, color, effects, etc.)
- **WebSocket**: `ws://<device-ip>/ws` — real-time bidirectional state updates
- **CORS**: Fully supported — browser-based apps can connect directly to WLED devices on the local network
- **Info endpoint**: `http://<device-ip>/json/info` — device info, version, LED count, etc.
- **Effects list**: `http://<device-ip>/json/effects` — array of all available effect names
- **Palettes list**: `http://<device-ip>/json/palettes` — array of all available palette names

## Editing Tips
- To add real screenshots: search for `img-placeholder` divs, replace with `<img>` tags
- Each placeholder has a descriptive label — match your screenshot to the label
- Recommended image sizes: wide placeholders = 16:9, tall (phone screenshots) = 3:4
- Keep images in an `img/` subfolder if adding them locally
