# Kodnyx Website (kodnyx.com)

Statische Website, gehostet auf GitHub Pages. Kein Build-Schritt, kein
Framework, kein Paketmanager — reines HTML mit inline `<style>` und `<script>`.

## Deployment

**Push auf `main` = live auf kodnyx.com.** Es gibt keine Staging-Stufe und
keinen CI-Schritt. Jeder Commit auf `main` ist nach ~1 Minute öffentlich.
Entsprechend vorsichtig pushen und vorher lokal ansehen.

## Remotes

| Remote   | Repo                                   | Rolle |
|----------|----------------------------------------|-------|
| `origin` | `kodnyx13/kodnyx13.github.io`          | **Das Live-Repo** (Firmen-Org). Bedient `kodnyx.com` seit dem Cutover am 28.08.2026. HTTPS wird erzwungen. |
| `old`    | `kodnyx-kris/kodnyx-kris.github.io`    | Altrepo, Privat-Account, ohne Domain. Nur noch Historie; Push-URL ist absichtlich deaktiviert. |

- **Die Datei `CNAME` (Inhalt `kodnyx.com`) gehört jetzt ins Repo** — GitHub
  hat sie beim Setzen der Domain selbst angelegt. Nicht löschen.
- **Das Repo muss public bleiben.** `kodnyx13` ist auf dem GitHub-Free-Plan,
  dort gibt es Pages nur für öffentliche Repos.

DNS liegt bei IONOS und wird ausschließlich von Kristoffer geändert.
Apex-A-Records zeigen auf die GitHub-Pages-IPs (185.199.108–111.153).

## Lokale Vorschau

Über das Browser-Pane, Konfiguration in `.claude/launch.json`
(`python -m http.server` auf Port 4173). Vor jedem Push auf `main` ansehen.

## Struktur

- `index.html` — die Relaunch-Seite (DC Explorer). One-Pager mit Anker-Nav,
  Design-Tokens in `:root`, DE default + EN-Toggle (`.de`/`.en`-Spans,
  Klasse `lang-en` auf `body`), Cookie-Banner mit Opt-in-GA.
- `imprint.html`, `datenschutz.html` — Rechtstexte, eigenes Nav zurück zu `index.html`
- `assets/` — Bilder der Relaunch-Seite (Partner-Logos, Referenz-Logos, Favicons)
- `app/` — Demos (`dc_diagnostic_demo.html`, `smartere-demo.html`) plus
  Hersteller-Logos. **`app/smartere-demo.html` wird in Outreach-Mails als
  Demo-Link verschickt und muss erreichbar bleiben.**
- Die Altstände (alter Einspar-Rechner, `index_old.html`, `test.html`, Decks
  usw.) wurden im August 2026 gelöscht; alles liegt in der Git-Historie.

## Textregeln

- Keine Gedankenstriche (– / —) im Seitentext, DE wie EN. Komma, Doppelpunkt
  oder Punkt stattdessen.
- E-Mail-Adressen stehen nie im Klartext im Quelltext; alle Mail-Links werden
  per JS zusammengesetzt (Klasse `.mail-link` bzw. Inline-Script im Impressum).
- Kein pauschaler Spar-Prozentsatz, keine Preise, nichts als "validiert"
  bezeichnen; nur Hartig und Phenogy sind namentlich nennbare Kunden.

## Design

Tokens stehen in `index.html` unter `:root` — Teal `#0E4C52`, Teal-Light
`#5FB7B0`, Orange `#F79646`, Schrift Plus Jakarta Sans (Google Fonts).
Verbindliche Marken-Vorgaben:
`C:\Users\krist\OneDrive\Dokumente\Claude Cowork\PROJECTS\kodnyx-brand-ci.md`

## Externe Abhängigkeiten

- **Google Analytics** GA4 `G-WJ4861VRQT` — lädt erst nach Einwilligung im
  Cookie-Banner (Opt-in; Ablehnung = lädt nie). Consent-Key im localStorage:
  `cookie-consent`.
- **Google Fonts** (Plus Jakarta Sans)
- Der alte Rechner-Worker (`kodnyx-calculator.kristoffer-285.workers.dev`,
  privater Cloudflare-Account) wird von der Seite nicht mehr genutzt, existiert
  aber noch.

## Bekannte Baustellen

- Die Domain ist bei GitHub für die Org `kodnyx13` **nicht verifiziert**
  (kein `_github-pages-challenge`-TXT-Record bei IONOS) — nachholen, schützt
  gegen Domain-Übernahme.
- Der `www`-CNAME bei IONOS zeigt noch auf `kodnyx-kris.github.io`. Funktioniert
  (GitHub routet über den Host-Header), sollte aber auf `kodnyx13.github.io`
  umgestellt werden.
- Altrepo `kodnyx-kris/kodnyx-kris.github.io` ist noch nicht archiviert.
