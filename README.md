# Kingdom Ads — site marketing

Site statique avec build Tailwind CSS pour Netlify.

## Développement local

```bash
npm install
npm run dev      # watch — recompile assets/styles.css à chaque sauvegarde
```

Ouvrir ensuite `index.html` (ou un petit serveur statique : `npx serve` / `python3 -m http.server`).

## Build production

```bash
npm run build    # génère assets/styles.css minifié
```

Sur Netlify, le build s'exécute automatiquement via `netlify.toml` (`command = "npm run build"`).

## Structure

- `index.html` — page unique
- `src/styles.css` — entrée Tailwind (@tailwind base/components/utilities)
- `tailwind.config.js` — thème (couleurs, fontFamily, fontSize custom)
- `assets/styles.css` — sortie compilée (générée, gitignorée si vous voulez)
- `input/` — images source (alex, william)
- `robots.txt`, `sitemap.xml`, `site.webmanifest`, `favicon.svg`, `humans.txt`, `browserconfig.xml` — fichiers SEO
- `_headers`, `_redirects`, `netlify.toml` — config Netlify

## Assets à fournir

Pour un SEO et PWA complets, créer dans la racine :

- `og-image.jpg` — 1200×630 px (partage social Open Graph / Twitter)
- `apple-touch-icon.png` — 180×180 px
- `favicon.ico` — fallback navigateurs anciens
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` — PWA
- `logo.png` — 512×512 px (utilisé dans JSON-LD)

## Mise en production sur un autre domaine

Chercher/remplacer `pub-kads.netlify.app` partout :

```bash
grep -rl "pub-kads.netlify.app" . --include="*.html" --include="*.xml" --include="*.txt" --include="*.json" --include="*.webmanifest" \
  | xargs sed -i 's/pub-kads.netlify.app/votre-domaine.fr/g'
```
