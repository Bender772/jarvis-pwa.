# JARVIS PWA prototype (v0.1.0)

A mobile-first, installable Progressive Web App prototype built with HTML, CSS and JavaScript.

## What works now
- Futuristic responsive chat interface
- Offline local commands: `help`, `time`, `date`, `status`
- IndexedDB local memory: `save note: ...`, `notes`, `add task: ...`, `tasks`, `complete task 1`
- Export notes and tasks as JSON
- Clear conversation without deleting saved memory
- Explicit erase-memory action with confirmation
- Service worker app-shell caching for offline launches after first successful load

## Important limitations
- This is a local prototype, not a connected AI assistant yet.
- It does not call any AI API and contains no API keys.
- Online availability indicator means the browser has a network connection; it does not mean AI is connected.
- Local memory is stored in this browser on this device. Clearing browser site data may remove it. Export important notes regularly.
- Service workers and PWA installation require HTTPS (or localhost during development).
- Google Fonts are optional and may not load offline; system fonts will be used as fallback.

## Files
- `index.html` — app structure
- `styles.css` — visual styling
- `app.js` — chat behavior, local commands and IndexedDB
- `manifest.webmanifest` — PWA metadata
- `sw.js` — offline app-shell cache
- `icons/jarvis.svg`, `icons/jarvis-192.png`, `icons/jarvis-512.png` — app icons

## Phone-only deployment (GitHub Pages)
1. Extract the ZIP on your phone with a file manager that supports ZIP files.
2. In your browser, sign in to GitHub and create a new public repository, e.g. `jarvis-pwa`.
3. Upload all files and the `icons` folder to the repository root. Do not upload the ZIP as the only file.
4. In the repository, open **Settings → Pages**.
5. Under build/deployment, select **Deploy from a branch**, choose `main` and `/(root)`, then save.
6. Wait for GitHub Pages to publish the site. Open the URL it shows, usually `https://YOUR-USERNAME.github.io/jarvis-pwa/`.
7. Open that URL in Chrome on the Redmi 14C. Test `help`, `save note: test`, `notes`, `add task: test task`, and `tasks`.
8. In Chrome, use the three-dot menu → **Add to Home screen** or **Install app** if offered.
9. Open JARVIS once while online so the service worker can cache the app shell. Then test by switching on Airplane mode and reopening it.

## Alternative: Netlify Drop
If available on your phone, sign in to Netlify and use its manual deploy/drop feature to upload the *extracted folder contents*. Keep the full directory structure. Use the HTTPS URL it provides, then add it to the home screen.

## Updating
Upload changed files to the same repository and wait for the deployment to finish. If the app appears unchanged, close it and reopen it; a service worker may retain the previous cached version. If needed, clear that site's data in Chrome (this also deletes its local JARVIS memory).

## Next milestone: secure online AI
Do not put an API key in `app.js`, `index.html`, or any other client file. The next stage should create a small backend endpoint that stores the secret as a server-side environment variable, validates requests, limits usage, and forwards prompts to the chosen AI provider.
