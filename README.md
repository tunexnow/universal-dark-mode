
# Universal Dark Mode - TuNeX

Force a clean, readable **dark mode** on (almost) any site.  
It auto-detects if a website already has a native dark theme, gives you **two algorithms**, and remembers your **per‑site** preference.

- **Palette (Clean):** semantic dark palette using CSS variables for best readability.
- **Filter (Safe):** page inversion with media re‑inversion for stubborn, image‑heavy layouts.
- **Auto mode:** chooses the better one per page; if the page is already dark, it does nothing.
- **Per‑site toggle** + mode via popup.
- **Shadow DOM aware** (for open roots).

> Built by **Abdulrasaq Babatunde (aka TuNeX)** - free to use & edit.

## Install (Dev / Unpacked)
1. Download this repository as a ZIP and extract, or `git clone` it.
2. Open Chrome / Edge → `chrome://extensions` → enable **Developer mode**.
3. Click **Load unpacked** → select the folder.
4. Pin the extension → open any site → click the icon to toggle & pick algorithm.

## How it works
- **Palette mode** adds `.__tunex_dark_palette__` on `<html>` and applies a carefully tuned dark palette using CSS variables. It keeps images/videos untouched to preserve color accuracy.
- **Filter mode** adds a CSS filter (`invert + hue-rotate`) on the entire page and re‑inverts media (images, videos, canvases, SVG, YouTube/Vimeo iframes). It’s more compatible with complex backgrounds.
- **Auto mode** samples background luminance and checks if the page is image/background‑heavy to pick the safer algorithm. If the page is already dark, it applies nothing.

## Repo structure
```
tunex-universal-dark-mode/
├─ manifest.json
├─ background.js           # default settings (install), storage schema
├─ src/
│  ├─ content.js           # main logic + auto detection + shadow DOM support
│  └─ algos/
│     └─ palette.css       # palette-based global dark theme
├─ popup.html
├─ popup.js
├─ options.html
├─ options.js
└─ assets/
   └─ icons/               # 16/48/128 pngs (placeholders)
```

## Known good behavior
- Works on most news/blog/docs/web apps.
- Skips well-known native-dark giants by default (`x.com`, `twitter.com`, `youtube.com`, `twitch.tv`). You can still enable manually via the popup.

## Tips for perfect results
- If a site looks washed out, switch to **Palette**.
- If a site has lots of textured backgrounds or sprite sheets, use **Filter**.
- You can expand the **exclude list** in `background.js` or add site-specific rules in `content.js`.

## License
MIT - do anything, just keep the attribution.
