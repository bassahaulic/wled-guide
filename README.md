# Bassahaulic WLED Setup Guide

A beginner-friendly walkthrough for customers setting up WLED on the **Gledopto GL-C-016WL-D** ESP32 controller with **WS2811** LED strips.

## Quick Start

Open `index.html` in any browser — no server or build step needed.

## What's Included

| Section | Description |
|---------|-------------|
| Hero | Welcome banner with Bassahaulic branding |
| What You'll Need | Checklist of required hardware |
| Step 1: Wiring | GPIO16 wiring diagram for WS2811 (12V) |
| Step 2: Connect to WLED-AP | First-time WiFi hotspot connection |
| Step 3: Configure Home WiFi | Join your home network |
| Step 4: Download the App | iOS App Store + Android GitHub links |
| Step 5: Configure LED Strip | WS2811 type, count, GPIO, color order |
| Step 6: Effects & Presets | Color picker, 186+ effects, presets, segments |
| Bonus: Microphone | Audio-reactive I2S mic configuration |
| Bonus: Relay | GPIO 12 power-saving relay setup |
| Troubleshooting | Button functions, common issues, factory reset |
| Controller Specs | Gledopto GL-C-016WL-D quick reference card |

## Bassahaulic WLED Controller (PWA)

The `app/` directory contains a Progressive Web App for controlling WLED devices directly from your phone or browser.

### Features
- **Direct WLED control** — connect to any WLED device on your local network via JSON API and WebSocket
- **Network scan** — automatically discover WLED devices on your subnet
- **Installable PWA** — add to home screen on iOS and Android for a native app experience
- **Offline shell** — service worker caches the app shell (network required for WLED communication)
- **Matrix rain background** — animated falling character canvas for Bassahaulic brand aesthetic
- **Glassmorphism UI** — frosted glass panels with backdrop blur effects

### Design System
- **Background**: `#000000` | **Accent**: `#e21aff` | **Blue**: `#0097ff`
- **Text**: `#ffffff` | **Muted**: `#cccccc`
- **Fonts**: Audiowide (brand headings), Orbitron (secondary headings/labels), Roboto (body)

## Features

- **Sticky progress nav** — scroll-tracking dots show your place in the guide
- **Copy-to-clipboard** — tap `WLED-AP`, `wled1234`, or `4.3.2.1` to copy instantly
- **Collapsible sections** — bonus topics hidden by default to keep it simple
- **Mobile-first** — designed for use on a phone while setting up
- **Dark theme** — Bassahaulic brand colors (magenta `#e21aff`, blue `#0097ff`, black `#000000`)
- **Zero dependencies** — single HTML file, works offline (after font load)

## File Structure

```
LED/
├── index.html          # Complete setup walkthrough page
├── CLAUDE.md           # Project conventions & reference
├── README.md           # This file
└── app/                # PWA — Bassahaulic WLED Controller
    ├── index.html      # PWA main interface
    ├── manifest.json   # PWA manifest (name, icons, theme)
    ├── sw.js           # Service worker for offline caching
    └── icons/          # PWA icons (192x192, 512x512)
```

---

## TODO — Remaining Work

### High Priority
- [ ] **Add real screenshots** — 13 image placeholders need actual photos/screenshots:
  - [ ] Wiring photo: Gledopto controller connected to WS2811 strip (GPIO16)
  - [ ] Phone WiFi list showing "WLED-AP" network
  - [ ] WLED web interface WiFi configuration page
  - [ ] WLED app home screen with "+" button
  - [ ] WLED app "Discover Lights" screen
  - [ ] WLED app "Found WLED!" confirmation
  - [ ] WLED Config → LED Preferences → Hardware Setup page
  - [ ] WLED color picker / main control UI
  - [ ] WLED effects list browser
- [ ] **Create `img/` folder** and optimize images (compress, resize to ~800px wide max)

### Medium Priority
- [ ] **Add Bassahaulic logo** to hero section and/or progress nav
- [ ] **Add favicon** — branded `.ico` or `.png`
- [ ] **Customize footer link** — point "Bassahaulic" link to actual website URL
- [ ] **Add LED count reference** — table of common WS2811 strip lengths and LED counts sold
- [ ] **Add power supply sizing guide** — quick formula: (LED count x 0.06A) for customer reference
- [ ] **Review wiring color callouts** — confirm wire colors match the specific WS2811 strips you sell

### Low Priority / Nice-to-Have
- [ ] **Add a wiring diagram SVG** — visual pin diagram of the Gledopto controller
- [ ] **Add second output section** — guide for using GPIO2 as a second strip output
- [ ] **QR code** — link to this page that can be printed and included with shipments
- [ ] **Print stylesheet** — `@media print` styles for customers who want a paper copy
- [ ] **Analytics** — add lightweight tracking to see which steps users spend time on
- [ ] **Video embeds** — optional YouTube tutorial links for visual learners
- [ ] **Home Assistant section** — brief guide on WLED + Home Assistant integration
- [ ] **OTA update section** — how to update WLED firmware through the web interface

### PWA — Bassahaulic WLED Controller
- [ ] **Add real Bassahaulic logo/icon for PWA** (replace placeholder icons in `app/icons/`)
- [ ] **Test PWA install on iOS and Android**
- [ ] **Test WLED connection with real Gledopto controller**
- [ ] **Test network scan feature**
- [ ] **Add segments support** (future enhancement)
- [ ] **Add playlist builder** (future enhancement)
- [ ] **Add multi-device control** (future enhancement)

### Content Verification
- [ ] **Test full walkthrough** — follow the guide end-to-end with a fresh controller to verify accuracy
- [ ] **Confirm WS2811 color order** — verify RGB vs GRB with the specific strips being sold
- [ ] **Verify iOS app name** — confirm "WLED" or "WLED Native" is correct for current App Store listing
- [ ] **Check Android APK link** — verify GitHub releases URL is current

---

## Hosting

This is a static HTML file. Host it anywhere:
- Drop into any web server directory
- Upload to GitHub Pages, Netlify, Vercel, etc.
- Serve from your existing Bassahaulic website
- Open directly from a local file (`file://`)

**Note:** The PWA (`app/`) requires HTTPS for service worker registration when hosted remotely. `localhost` works without HTTPS for development.

## License

Internal use — Bassahaulic customer documentation.
