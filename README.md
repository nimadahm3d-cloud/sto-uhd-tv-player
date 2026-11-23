# STO People's Choice UHD TV Player — v1.0

A lightweight, muted, fullscreen-style video playlist for Samsung and LG smart-TV web browsers. Open the **same URL** on each TV. Each TV plays the **same playlist independently** (not frame-synchronized).

## Quick start
1. Upload `index.html` and `playlist.json` to the same folder on a static HTTPS host (e.g., GitHub Pages, Cloudflare Pages, Netlify). Make the site public.
2. Open the published `index.html` URL on a TV. If autoplay is blocked, click **Start display** once using the TV remote.
3. Put the TV browser in fullscreen / hide its toolbar if supported. Keep the browser open.
4. Open the same URL on the remaining TVs. The playlist loops continuously.

## Test on a computer first
In this folder, run `python -m http.server 8000` then visit `http://localhost:8000` (do not open the HTML directly as a file).

## Replace the demo clips with real 4K footage
The included **demo videos are HD, NOT UHD**. They are included only to demonstrate a working playlist. Obtain your own appropriately licensed **3840 × 2160** video files and host them at publicly accessible direct HTTPS MP4 URLs (not a stock-footage webpage, share page, or YouTube link). Edit `playlist.json` and replace each `src` with a direct video URL; set `title` as desired. You can add or remove entries. TVs check for playlist changes every 120 seconds and switch to the new playlist if the video list changes.

For maximum Samsung/LG compatibility, test MP4/H.264 + AAC (or no audio) first. Some TV models support HEVC/H.265 for efficient 4K, but support varies by year/model. All playback is muted. Keep file bitrates suitable for store bandwidth. The browser's video decode limits may prevent UHD on some models.

## Bandwidth warning
6–15 TVs each stream their own video. At 15 Mbps per 4K stream, 15 TVs can consume roughly **225 Mbps** continuously, excluding overhead. For stable operation, use a local HTTP media server/cache on the store LAN, or lower bitrates and test on your actual TV models. Free static site hosting typically cannot economically serve high-volume 4K video files; host the player for free and video media separately.

## Notes and limitations
- No login or admin dashboard in v1.0: edit `playlist.json` to manage clips.
- This version **does not synchronize frames** between TVs.
- Automatic autoplay may require initial user interaction and may not resume after a TV is turned off or its browser is closed.
- For local network use, serve both files and videos from an always-on local PC/server with an HTTP server, then point each TV to its LAN IP and port. Make sure TVs can reach that IP.
- Playlist refresh applies when changed; the TV must be able to reach the manifest URL.
- The sample clips are demonstration material, not a curated retail display or a guarantee of 4K quality or commercial licensing for your intended usage. Replace before deployment.
