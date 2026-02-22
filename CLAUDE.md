# ERIMEC — Projektkontext für Claude

## Projektbeschreibung
Astro-Website für **ERIMEC Messgeräte Handel** — ein fiktiver/realer Händler für Präzisionsmessgeräte (Temperatur, Druck, Strahlung, Spezial). Gegründet 1998, 1.200+ Produkte.

## Tech-Stack
- **Framework:** Astro 5.x (statisch, kein SSR)
- **Styling:** Tailwind CSS v4 (via `@tailwindcss/vite`)
- **Fonts:** Bebas Neue (Display), DM Sans (Body) — Google Fonts
- **Deployment:** GitHub Actions → `dist/` direkt im `main`-Branch, Shared Hosting (kein Node.js/Passenger)
- **Build:** `npm run build` → `dist/`

## Dateistruktur
```
src/
  layouts/Layout.astro     — Globales Layout, Nav, Footer
  pages/
    index.astro            — Startseite (Hero, Stats, Kategorien, Features, CTA)
    produkte.astro         — Produktübersicht
    kontakt.astro          — Kontaktformular
    impressum.astro        — Impressum
    datenschutz.astro      — Datenschutz
  styles/global.css        — Tailwind + Custom Properties (Farben, Animationen)
public/
  favicon.svg
  .htaccess               — Passenger deaktiviert, statisches Routing
dist/                     — Build-Output, wird direkt deployed
```

## Design-System
- **Hintergrund:** `#0b0b10` (fast schwarz)
- **Akzentfarbe:** `#C8820A` (Amber/Gold) — CSS-Klasse `amber`
- **Textfarben:** `text`, `text-dim`, `muted`
- **Borders:** `border-line`, `bg-surface`
- **Fonts:** `font-display` = Bebas Neue, `font-sans` = DM Sans
- **Stil:** Industrial / Precision Instruments — dark theme, crosshairs, tech-aesthetic

## Deployment
- GitHub Actions: `.github/workflows/deploy.yml`
- Bei Push auf `main`: `npm run build`, dann `dist/` via FTP deployen
- `.htaccess` im `public/`-Ordner: Passenger deaktiviert, `DirectoryIndex index.html`, Fehlerseiten

## Wichtige Entscheidungen
- Kein Node.js auf dem Hosting → statischer Build
- `dist/` liegt im `main`-Branch (kein separater `gh-pages`-Branch)
- Tailwind v4 (nicht v3) — Konfiguration via CSS, nicht `tailwind.config.js`

## Workflow
1. Entwicklung: `npm run dev`
2. Build testen: `npm run build && npm run preview`
3. Deploy: `git push origin main` → GitHub Actions übernimmt
