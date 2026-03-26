# Hackathon CMD 2026

An interactive, space-themed information experience created for the HvA CMD Hackathon 2026.  
The content is based on information from [Nebula Xplorer / SRON](https://www.sron.nl/en/).

This project is built with **SvelteKit** and features:

- an animated overview page with orbiting research-question cards,
- dynamic detail pages generated from local JSON content,
- a black hole interaction that leads to an easter egg scene.

## Features

- **Animated overview (`/`)**
  - Orbiting cards and satellites around a central black hole.
  - Physics-inspired motion (orbiting, falling, respawn behavior).
  - Card links route to detail pages.
- **Detail pages (`/onderzoeksvragen/[slug]`)**
  - Dynamic route loading based on card title slugs.
  - Content, optional list items, and image metadata from `static/cards.json`.
- **Easter egg (`/easteregg`)**
  - Animated alien sequence using GSAP + MorphSVGPlugin.
- **View transitions**
  - Navigation transitions are enabled via `document.startViewTransition` when available.

## Tech Stack

- **SvelteKit** (Svelte 5)
- **Vite**
- **GSAP** (including MorphSVG plugin usage in the alien animation)
- Plain CSS (component-level and shared styles)

## Project Structure

- `src/routes/+page.svelte` - overview page
- `src/routes/+page.ts` - loads card data
- `src/routes/onderzoeksvragen/[slug]/+page.svelte` - detail page UI
- `src/routes/onderzoeksvragen/[slug]/+page.ts` - slug matching and detail data loading
- `src/routes/easteregg/+page.svelte` - easter egg page
- `src/lib/components/BlackHoleInfoPage.svelte` - main black-hole/canvas/card interaction
- `src/lib/components/aliencomponent.svelte` - alien animation sequence
- `src/lib/components/viewtransition.svelte` - view transition hook
- `static/cards.json` - research card content
- `static/sattelites.json` - orbiting satellite/emoji config

## Getting Started

### 1) Install dependencies

```bash
npm install
```

### 2) Start development server

```bash
npm run dev
```

Then open the local URL shown in your terminal.

## Available Scripts

- `npm run dev` - start local dev server
- `npm run build` - create production build
- `npm run preview` - preview production build locally

## Deployment (Cloudflare)

This project is hosted on **Cloudflare**.

- If Cloudflare Pages is connected to your Git branch, deploy by pushing to the configured branch.
- To verify the production build locally before deploying:

```bash
npm run build
npm run preview
```

## Notes

- Card slugs are generated from titles (lowercase + hyphenated).
- The project currently uses the filename `sattelites.json` (as referenced in code).
