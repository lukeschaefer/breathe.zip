# breathe.zip

A minimal box-breathing web app. The exercise cycles continuously:

- Inhale: 5 seconds
- Hold (full): 5 seconds
- Exhale: 5 seconds
- Hold (empty): 5 seconds

### UI
- A centered square box with a white border
- A circle inside that expands to fill the box on inhale, stays full on hold, collapses on exhale, and stays empty on hold
- A gently animated, colorful gradient background

### Implementation notes
- The animation is driven purely by CSS keyframes in `src/style.css`.
- Markup is defined in `index.html`; `src/main.ts` only imports styles.
- Adjust these CSS variables in `:root` to change behavior:
  - `--cycle-duration`: total length of the 4-phase loop (default `20s`)
  - `--min-scale`: circle scale at empty (default `0.2`)
  - `--max-scale`: circle scale at full (default `1`)
  - `--box-glow-scale`: box scale during full hold (default `1.15`)
  - `--box-glow`: drop-shadow filter during full hold

### Run locally
```bash
npm install
npm run dev
```

### Build for production
```bash
npm run build
npm run preview
```

### PWA & Offline
- The app is installable and works offline via a service worker generated at build time using `vite-plugin-pwa`.
- During `npm run preview` the service worker is active; assets and `index.html` are precached so the app loads offline.
- Updates: the service worker auto-updates in the background on new deploys.

#### Development notes
- No service worker runs in `npm run dev`. Test PWA in `npm run preview` or after deploying.
- Icons can be updated in `public/` and referenced in the PWA manifest (see `vite.config.ts`). 