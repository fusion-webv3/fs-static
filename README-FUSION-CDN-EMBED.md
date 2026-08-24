# FUSION CDN-origin Service Worker runtime

This version uses the Arctic-style `embed.svg` architecture for local `file://` launches.

## Runtime flow

`file://.../index.html`
→ `https://cdn.jsdelivr.net/gh/fusion-webv3/fs-static@main/embed.svg`
→ CDN-origin iframe `srcdoc`
→ Scramjet runtime
→ `navigator.serviceWorker.register(CDN/s.js, {scope: CDN/})`
→ Scramjet proxy frame

The top-level FUSION page never calls `navigator.serviceWorker.register()`.
The native Service Worker is registered by the HTTPS CDN-origin runtime.

## Deployment

The repository must be available at:

`https://cdn.jsdelivr.net/gh/fusion-webv3/fs-static@main/`

The following files are required by the CDN runtime:

- `embed.svg`
- `sw.js`
- `scramjet-engine/*`
- `bare-mux/*`
- `transport/*`

`index.html` is still the local/top-level FUSION UI and can be opened from `file://`.
