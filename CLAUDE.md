# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page website for **Lake Como Venture Lab**, a deep tech startup acceleration program by Confindustria Lecco e Sondrio, in partnership with Politecnico di Milano (Polo Territoriale di Lecco) and Camera di Commercio Como-Lecco.

The site is in Italian and targets deep tech startups in **mechatronics** and **MedTech**.

## Deployment

Hosted on **Cloudflare Workers** as a static assets site.

- Worker name: `lake-como-venture-lab`
- Live URL: `https://lake-como-venture-lab.federica-pasini91.workers.dev`
- Deploy config: `wrangler.jsonc` (points `assets.directory` to `./`)
- Deploys automatically on push to `main` via GitHub integration

No build step — the repo root is served directly as static assets.

## Architecture

Single file: `index.html` contains all HTML, CSS, and JS inline. No external frameworks, no bundler, no package manager.

**CSS structure** (all in `<style>` in `<head>`):
- CSS custom properties in `:root` define the color palette (pastel green/blue tones + dark teal/blue)
- Sections are independently styled with class prefixes: `.offer-*`, `.focus-*`, `.phase-*`, `.lab-*`, `.mentor-*`, `.stat-*`, `.discover-*`
- Responsive via two breakpoints: `@media (max-width: 768px)` and `@media (max-width: 480px)`

**Page sections** (in order):
1. Navbar (fixed, scroll-effect via JS)
2. Hero
3. CTA banner (value proposition: €50k/startup)
4. Program details (benefits list)
5. Quote
6. Focus areas (Meccatronica / MedTech)
7. Phases (4-phase 12-month timeline)
8. Mentors (placeholder cards — real names TBD)
9. Labs (3 Politecnico labs)
10. Territory stats + ecosystem cards
11. CTA final → links to f6s.com application
12. Discover more (podcast, event, press — links TBD)
13. Footer

**JavaScript** (inline at bottom): navbar scroll shadow toggle + IntersectionObserver for `.fade-in` scroll animations.

**External dependencies**: Google Fonts only (Inter + Caveat), loaded via `<link>` in `<head>`.

## Key Details

- Application link: `https://www.f6s.com/lake-como-venture-lab` (used in navbar CTA, hero CTA, and final CTA)
- Mentor cards and "Scopri di più" links are placeholder — real content pending
- Logo is an inline SVG representing the Lake Como silhouette
- `ipotesi logo.png` in the repo root is a logo concept (not currently used in HTML)
