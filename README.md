# RANAVision — Battle Intelligence Map

A real-time military intelligence dashboard built as a single-file web app. Two interactive world map modes powered by D3.js v7 — explore active conflict zones and global military arsenals with zero backend required.

## Live Demo

Open `index.html` directly in any modern browser — no build step, no server, no dependencies to install.

## Modes

### Conflict Map
- 20 active conflict zones highlighted in pulsing red
- Hover any country for a quick tooltip
- Click a conflict country to open a detailed intel drawer (status, casualties, weapons used, key factions, territory, latest developments)

### Arsenal Map
- 29 countries color-coded by military tier (Gold → Tier 1 superpowers, Orange → Tier 2 regional powers, Grey → Tier 3)
- Click any country to open a full-screen arsenal overlay
- 6 weapon category tabs: War Weapons, War Vehicles, War Jets, War Ships, Nuclear Weapons, Other
- Click any weapon card to open a hero view with full specs and stats

## Tech Stack

| Layer | Technology |
|---|---|
| Map | D3.js v7 + TopoJSON (world-atlas@2) |
| Projection | geoNaturalEarth1 with zoom/pan |
| Fonts | Bebas Neue + Courier Prime (Google Fonts) |
| Flags | FlagCDN (flagcdn.com) |
| Styling | Vanilla CSS with animations |
| Data | Hardcoded JS objects (no API) |

## Color Palette

```
#080808  — Background black
#FF2020  — Conflict red / accent
#3A3A3A  — Mid grey
#E8E8E8  — Off-white text
#FFD700  — Tier 1 gold
#FF8C00  — Tier 2 orange
```

## Data Coverage

**Conflicts (20):** Ukraine, Gaza, Sudan, Myanmar, Yemen, Ethiopia, Haiti, Mali, Niger, Somalia, DRC, Nagorno-Karabakh, Syria, Iraq, Afghanistan, Pakistan, Kosovo, Taiwan Strait, North Korea, Mozambique

**Arsenals (29):** USA, Russia, China, India, UK, France, Pakistan, Israel, North Korea, South Korea, Japan, Germany, Turkey, Iran, Saudi Arabia, Ukraine, Australia, Taiwan, Brazil, Italy, Poland, Canada, Egypt, Indonesia, Singapore, UAE, Vietnam, Thailand, Sweden

## GitHub Pages Deployment

1. Push this repo to GitHub
2. Go to Settings → Pages
3. Set Source to **GitHub Actions**
4. Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - id: deployment
        uses: actions/deploy-pages@v4
```

5. Push to `main` — GitHub Actions will deploy automatically.

## Structure

```
RANAVision/
└── index.html    # Entire app — HTML + CSS + JS, fully self-contained
```
