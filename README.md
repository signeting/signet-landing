# Signet Landing

Static React + TypeScript landing page for https://signet.ing, built with Vite + Motion and styled via Tailwind. This repo contains only the frontend; deployment is handled via GitOps.

## Requirements
- Node.js 18+
- npm (ships with Node)

## Install & Build
```bash
npm install
npm run build
```

The production build is emitted to `dist/` (set via `vite.config.ts`). The output can be copied to any static host (nginx, S3/CloudFront, etc.).

## Develop
```bash
npm run dev
```

Runs Vite dev server (default http://localhost:3000/) with hot reload.

## Assets & SEO
- OG image, favicons, and touch icons live in `src/public/`.
- Helpers to generate PNG assets from SVGs: `src/create-og-image.html` and `src/create-icons.html`.
- Meta tags and structured data are defined in `src/index.css` + `src/App.tsx`.

## Deploying to a static host (nginx example)
- Copy `dist/` contents to your web root (e.g., `/usr/share/nginx/html/signet.ing`).
- Configure SPA routing fallback:
  ```nginx
  location / { try_files $uri $uri/ /index.html; }
  ```
- Optional: cache-bust static assets under `/assets/` with long-lived headers.

## Repo status
- Origin: extracted from the `signet-trailer/` folder in github.com/bitiq-io/gitops.
- Source of truth for the landing UI lives here; GitOps repos consume the built artifact/image.
- License: MIT (see `LICENSE`).
