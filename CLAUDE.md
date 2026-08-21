# Kodnyx Website (kodnyx.com)

Statische Website, gehostet auf GitHub Pages. Kein Build-Schritt, kein
Framework, kein Paketmanager — reines HTML mit inline `<style>` und `<script>`.

## Deployment

**Push auf `main` = live.** Es gibt keine Staging-Stufe und keinen CI-Schritt.
Jeder Commit auf `main` ist nach ~1 Minute unter der jeweiligen Pages-URL
öffentlich. Entsprechend vorsichtig pushen.

## Remotes — wir sind mitten im Umzug

| Remote   | Repo                                   | Rolle |
|----------|----------------------------------------|-------|
| `origin` | `kodnyx13/kodnyx13.github.io`          | **Zielrepo**, Firmen-Org. Hier wird entwickelt. Preview: `https://kodnyx13.github.io` |
| `old`    | `kodnyx-kris/kodnyx-kris.github.io`    | Altrepo, Privat-Account. Bedient aktuell **die Live-Domain `kodnyx.com`**. Nur noch für Hotfixes. |

Die Umstellung der Custom Domain auf `origin` passiert erst zum Launch des
Redesigns. Bis dahin gilt:

- **Die Datei `CNAME` darf in `origin` nicht existieren.** Sonst streiten sich
  altes und neues Repo um `kodnyx.com`. Die Domain wird am Launch-Tag über die
  Repo-Settings gesetzt, GitHub schreibt die Datei dann selbst.
- **Das Repo muss public bleiben.** `kodnyx13` ist auf dem GitHub-Free-Plan,
  dort gibt es Pages nur für öffentliche Repos.

DNS liegt bei IONOS und wird ausschließlich von Kristoffer geändert.

## Lokale Vorschau

Über das Browser-Pane, Konfiguration in `.claude/launch.json`
(`python -m http.server` auf Port 4173). Vor jedem Push auf `main` ansehen.

## Struktur

- `index.html` — die eigentliche Seite. Alles in einer Datei: Design-Tokens in
  `:root`, Sections `#home`, `#about`, `#calculator`, Nav, Cookie-Banner,
  Rechner-Formular.
- `imprint.html`, `datenschutz.html` — Rechtstexte, eigenes Nav zurück zu `index.html`
- `app/` — Demos (`dc_diagnostic_demo.html`, `smartere-demo.html`) plus Hersteller-Logos
- `index_old.html`, `index2_pre_sticker.html`, `index_calc_coming_soon.html`,
  `test.html`, `waiting_list.html`, `investors.html`, `onepager.html`,
  `dc_check.html` — **Altstände**, nicht mehr verlinkt. Beim Redesign
  aussortieren, nicht versehentlich mitpflegen.

## Design

Tokens stehen in `index.html` unter `:root` — Teal `#0E4C52`, Teal-Light
`#5FB7B0`, Orange `#F79646`, Schrift Plus Jakarta Sans (Google Fonts).
Verbindliche Marken-Vorgaben:
`C:\Users\krist\OneDrive\Dokumente\Claude Cowork\PROJECTS\kodnyx-brand-ci.md`

## Externe Abhängigkeiten

- **Rechner-Backend**: Cloudflare Worker
  `https://kodnyx-calculator.kristoffer-285.workers.dev` (`/calculate`, `/submit`).
  Liegt auf einem **privaten** Cloudflare-Account — gleiches Umzugsthema wie das
  GitHub-Repo, noch offen.
- **Google Analytics** GA4 `G-WJ4861VRQT`, hinter dem Cookie-Banner
- **Formspree** für Formularversand
- **Google Fonts**

## Bekannte Baustellen

- Repo ist ~61 MB, darunter ein 6,5-MB-Foto (`DSC03355.jpg`) und ein 4,3-MB-Logo
  (`kodnyx_white_logo.png`). Ladezeit ist ein Redesign-Thema.
- „Enforce HTTPS" ist am Live-Repo **aus** — beim Cutover aktivieren.
- Die Domain ist bei GitHub **nicht verifiziert** (kein `_github-pages-challenge`
  TXT-Record) — beim Cutover für die Org `kodnyx13` nachholen.
