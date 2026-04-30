# Sky Striker

A retro SNES-style vertical shooter that runs as a Progressive Web App. Plays offline once installed.

![Sky Striker icon](icon-192.png)

## Play it

- **Desktop**: Arrow keys or WASD to move, `Z` / Space to shoot, `X` to bomb, `P` to pause, `M` to mute.
- **Mobile**: Drag anywhere on the screen to fly (the plane stays above your finger so it isn't hidden). Auto-fire while holding. Tap the BOMB button on the bottom-right.

## Deploy on GitHub Pages

1. Create a new public repo (e.g. `sky-striker`).
2. Drop these files in the repo root and push:
   ```
   index.html
   sw.js
   manifest.webmanifest
   favicon.png
   icon-192.png
   icon-512.png
   icon-512-maskable.png
   apple-touch-icon.png
   ```
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / root → Save**.
4. Wait a minute, then open `https://<your-username>.github.io/sky-striker/`.

That's it. Service worker uses relative paths, so it works fine on a subpath.

## Install as an app (offline play)

- **iOS Safari**: tap the Share button → **Add to Home Screen**.
- **Android Chrome**: menu → **Install app** (or **Add to Home Screen**).
- **Desktop Chrome/Edge**: install icon in the address bar.

After the first online load, the app shell and font are cached. You can fly with airplane mode on.

## Updating the game

Service worker uses a versioned cache (`sky-striker-v1`). When you change `index.html` or assets, bump the version in `sw.js`:

```js
const VERSION = 'sky-striker-v2';
```

Old caches get cleaned up on the next activation. Users may need to close and reopen the PWA to pick up the update.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole game (HTML, CSS, JS, sprites — all inlined) |
| `sw.js` | Service worker for offline caching |
| `manifest.webmanifest` | PWA manifest — name, icons, display mode |
| `icon-*.png` | App icons (192, 512, maskable, Apple) |
| `favicon.png` | Browser tab icon |

## License

Do whatever you want with it.
