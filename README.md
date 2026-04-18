# Pokédex Arena

**Live:** https://pokedex-area.wayna.co

Landing page de Pokémon con estética RPG-HUD: explorador de los 151 de Gen I con búsqueda, filtros por tipo, modal de detalle con radar hexagonal animado, modo comparar, toggle ES/EN y 3 temas (RPG / Arcade / Holo).

Datos en vivo desde [PokéAPI](https://pokeapi.co). Sprites desde el CDN oficial de PokéAPI.

## Stack

Sitio estático de un solo archivo (`index.html`). React 18 + Babel Standalone cargados desde `unpkg.com`; JSX se compila en el navegador. Sin build step.

## Dev local

Cualquier servidor estático sirve. Por ejemplo:

```sh
python3 -m http.server 8080
# o
npx serve .
```

Abrir `http://localhost:8080`.

## Deploy en Cloudflare Pages

### Opción A — Git integration (recomendado)

1. `git remote add origin <tu-repo>` y `git push -u origin main`.
2. En Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Selecciona el repo. Configuración:
   - **Framework preset:** `None`
   - **Build command:** (vacío)
   - **Build output directory:** `/`
4. Deploy. Cada push a `main` redeploya automáticamente.

### Opción B — Wrangler CLI

```sh
npx wrangler pages deploy . --project-name pokedex-arena
```

La primera vez pide login con tu cuenta de Cloudflare. Devuelve una URL `*.pages.dev`.

## Archivos

- `index.html` — app completa (CSS inline + React + JSX inline).
- `_headers` — cabeceras HTTP aplicadas por Cloudflare Pages (seguridad + no-cache del HTML).
- `.gitignore`
