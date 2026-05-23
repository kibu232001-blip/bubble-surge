# 🫧 Bubble Surge

> **Bubbles are rising. Colors are shifting. Tap fast or lose it all.**

An arcade bubble-tapping PWA game built with vanilla HTML5 Canvas. Match the target number and color before the timer runs out — chain correct taps for combo multipliers, survive 10 escalating levels.

---

## Gameplay

A target appears at the top of the screen:

```
TAP  [7]  IN  ● CRIMSON
```

Colorful soap bubbles rise from the bottom of the screen, each carrying a number. Your job:

- ✅ **Tap the correct number in the correct color** → score +N points
- ❌ **Tap the wrong bubble** → score −N points
- ⏱ **Timer runs out** → combo resets, new target appears
- 🔥 **Chain 3+ correct taps** → combo multiplier kicks in (×2 / ×3 / ×4)

---

## Features

- 🎮 Two modes — **Regular** (5s → 3s timer) and **Expert** (5s → 1s timer)
- 📈 10 levels — bubble count, speed, and spawn rate all escalate every 20 seconds
- 🎯 Guaranteed fairness — every target is always findable on screen
- 🔢 All 9 numbers stay represented — weighted spawning keeps the full set visible
- 🏆 High scores saved per mode (localStorage)
- 🔊 Web Audio sound effects — no audio files, generated in-browser
- 🌊 Animated underwater background — god rays, caustic shimmer, plankton particles
- 📱 Full PWA — installable, offline-capable, fullscreen portrait

---

## Tech Stack

| Layer | Detail |
|---|---|
| Rendering | HTML5 Canvas 2D API |
| Game loop | `requestAnimationFrame` |
| Audio | Web Audio API (procedural tones) |
| Storage | `localStorage` |
| Offline | Service Worker (cache-first) |
| Packaging | PWA → APK via PWABuilder |
| Hosting | GitHub Pages |

Zero dependencies. No frameworks. No build step. One HTML file.

---

## File Structure

```
bubble-surge/
├── index.html      # Full game — all logic, UI, canvas rendering
├── manifest.json   # PWA manifest (fullscreen, portrait, theme)
├── sw.js           # Service worker — offline caching
├── splash.jpg      # Menu background art
├── icon-192.svg    # App icon 192×192
├── icon-512.svg    # App icon 512×512 (maskable)
└── README.md
```

---

## Running Locally

No build step needed — just open the file:

```bash
# Option 1 — direct open
open index.html

# Option 2 — local server (recommended for SW + manifest to work)
npx serve .
# or
python3 -m http.server 8080
```

Then visit `http://localhost:8080`

---

## Deployment → APK

### 1. Deploy to GitHub Pages

- Push this repo to GitHub (public)
- Go to **Settings → Pages**
- Source: `main` branch, `/ (root)` folder
- Your live URL: `https://YOUR-USERNAME.github.io/bubble-surge`

### 2. Generate APK via PWABuilder

- Go to [pwbuilder.net](https://pwbuilder.net)
- Enter your GitHub Pages URL
- Click **Android → Generate Package**
- Download `.apk` (sideload) or `.aab` (Play Store)

### 3. Play Store (optional)

- Upload `.aab` to Google Play Console → Internal Testing
- Signing handled by Play App Signing
- Package ID: `com.kibuglobal.bubblesurge`

---

## Game Balance

| Level | Timer | Max Bubbles | Spawn Rate | Speed |
|---|---|---|---|---|
| 1 | 5.0s | 10 | 900ms | ~48 px/s |
| 5 | ~4.1s (reg) / ~3.0s (exp) | 19 | ~590ms | ~96 px/s |
| 10 | 3.0s (reg) / 1.0s (exp) | 28 | 280ms | ~145 px/s |

Combo multipliers: 3+ chain = ×2 · 5+ = ×3 · 7+ = ×4

---

## Roadmap

- [ ] Global leaderboard
- [ ] Daily challenge mode
- [ ] Haptic feedback (Android)
- [ ] Additional bubble skins / themes
- [ ] Timed sprint mode (60-second blitz)

---

## Credits

Built with [Claude](https://claude.ai) · Art generated with AI · Developed by **KibuglogalVentures LLC**

---

*Part of the KibuglogalVentures app portfolio alongside TransitionCommand and Going Out Global.*
