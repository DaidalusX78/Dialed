# Dialed 📻

<p align="center">
  <b>A sleek, lightweight web radio player bridging live broadcast audio and on-demand streaming discovery.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-v0.03-ff2a44.svg" alt="Version" />
  <img src="https://img.shields.io/badge/creator-Marc%20Bailey-black.svg" alt="Creator" />
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License" />
  <img src="https://img.shields.io/badge/dependencies-0-brightgreen.svg" alt="Zero Dependencies" />
</p>

---

## Overview

**Dialed** is a mobile-first, dependency-free web radio player designed for effortless listening and seamless music discovery. Currently tuned to **Chilli FM 91.5 (Marbella, Costa del Sol)**, Dialed couples live audio streaming with real-time metadata tracking, automatic high-res album artwork, and deep links to YouTube Music with a single click.

## Features

- 🎧 **Live Audio Streaming**: Low-latency, resilient HTML5 audio playback with real-time connection status indicators (Ready, Buffering, Streaming Live, Offline).
- 🖼️ **Dynamic Cover Artwork**: Queries the iTunes Search API in real time to fetch 600×600 high-resolution album artwork with in-memory caching and station logo fallback.
- 📱 **Media Session API (`navigator.mediaSession`)**: Displays current track title, artist, station, and album art directly on phone lock screens, smartwatches, and Bluetooth car dashboards with headphone play/pause controls.
- ⚡ **Real-Time Metadata (SSE & REST)**: Directly hooks into the broadcast provider's Server-Sent Events (SSE) feed (`streaming-api.aiir.com`) for instantaneous track updates, backed by an initial REST history lookup.
- 🎵 **One-Tap YouTube Music Search**: Formats the active track into a clean search query (`Artist Title`) that opens YouTube Music instantly.
- 🕒 **Session History (Recently Played)**: Rolling drawer tracking the last 10 songs played during the listening session, persisted in `localStorage` with individual YouTube Music links.
- 🔄 **Network & Mobile Lifecycle Resilience**: Automatic backoff reconnection on audio errors or Wi-Fi dropouts, with listeners for `online`/`offline` and tab visibility changes.
- ⚙️ **Configurable Stream URL**: Built-in settings drawer to override stream URLs on the fly or reset to defaults.
- 🚀 **Zero Dependencies**: 100% vanilla HTML5, CSS3, and JavaScript. Ready to deploy directly to GitHub Pages.

## Live Endpoints

| Resource | Endpoint | Description |
| :--- | :--- | :--- |
| **Audio Stream** | `https://stream.aiir.com/gzsyvjpqs4svv` | 128 kbps live MP3 stream |
| **Live Metadata (SSE)** | `https://streaming-api.aiir.com/mounts/metadata/subscribe/gzsyvjpqs4svv` | Real-time push events (`streamTitle`) |
| **Metadata History** | `https://streaming-api.aiir.com/mounts/metadata/history/gzsyvjpqs4svv/?limit=1` | REST endpoint for instant initial track lookup |
| **Artwork Lookup** | `https://itunes.apple.com/search` | Dynamic 600×600 album artwork |

## Getting Started

Because Dialed is completely self-contained, no installation or compilation is needed.

### Running Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/DaidalusX78/dialed.git
   cd dialed
   ```

2. Open `index.html` directly in your browser:
   - Double-click `index.html`, or
   - Launch a local lightweight web server:
     ```bash
     # Python 3
     python -m http.server 8000

     # Node.js
     npx serve .
     ```
3. Navigate to `http://localhost:8000` in your browser.

### Deploying to GitHub Pages

1. Go to your repository settings on GitHub (`https://github.com/DaidalusX78/dialed/settings/pages`).
2. Under **Build and deployment > Source**, select **Deploy from a branch**.
3. Choose the `main` branch and `/ (root)` folder, then click **Save**.
4. Your player will be live at `https://daidalusx78.github.io/dialed/`.

## Project Structure

```text
Dialed/
├── .gitignore              # Ignored files (local notes, WIP design assets)
├── README.md               # Project documentation
├── TODOLIST.md             # (Ignored) Development task tracking & log
└── index.html              # Main application (GitHub Pages ready)
```

## Author & Credits

Designed and developed by **Marc Bailey** ([@DaidalusX78](https://github.com/DaidalusX78)).

## Release History

* **v0.03 (Current)**: Dynamic iTunes album art, MediaSession API (lock screen/car play), Recently Played history drawer, mobile lifecycle resilience, `index.html` deployment.
* **v0.02**: Replaced broken stream URL with Aiir live stream, added real-time SSE metadata listener, and wired initial YouTube Music deep link.