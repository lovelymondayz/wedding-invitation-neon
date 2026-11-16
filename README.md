# wedding-invitation-neon

A single-page neon/cyberpunk-Minang wedding invitation for **Alifa & Daniel**
(#EXActlyforALIFA), built with pure CSS/SVG 3D — no WebGL, no JS frameworks.
One self-contained `index.html` — no build step, no backend, no database.

**Stack:** vanilla HTML/CSS/JS, SVG bride/groom figures extruded into 3D with
stacked CSS `translateZ` layers, glitch title, scroll-driven love-story scene,
live countdown, neon cursor glow, mouse parallax, shooting stars, drifting
neon particles, 3D card tilt and a countdown pop. All third-party assets
(fonts) are vendored under `vendor/`, so the page renders with no external
network access.

> This project is intentionally HTML-only. The fleet `CONSTITUTION.md` stack
> rules (Go + Gin + pgx + PostgreSQL + React/TS/Tailwind) do not apply here.

## Run

```bash
docker compose up -d --force-recreate
# http://localhost:3015
```

Any static file server pointed at this directory works too:

```bash
python3 -m http.server 3015
```

## Edit the content

Everything editable is inline in `index.html`:

- Couple names, date, venue — search for `Alifa`, `Daniel`, `05 · 12 · 2026`,
  `Dharmein Hotel`.
- Countdown target — the `2026-12-05T08:00:00+07:00` timestamp near the bottom.
- Love-story chapters — the `#chap` blocks in the **Our Love Story** section.
- Gift account — the bank (currently `BCA`), account name and account number in
  the **Wishes & Gift** section. **Confirm the account details before sharing
  the invitation.**

## Deploy

```bash
git push origin main
docker compose build --no-cache
docker compose up -d --force-recreate
```

## Files

```
index.html          the whole page (markup + styles + SVG 3D scene)
vendor/             self-hosted fonts (Orbitron, Rajdhani, Playfair Display)
nginx.conf          static hosting + cache headers
Dockerfile          nginx:alpine, no build stage
docker-compose.yml  single service on host port 3015
```
