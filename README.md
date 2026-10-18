# Y6 Filmmaking — The Film Studio

The Year 6 filmmaking pack: ten short comedy films, each in five colour-coded
stages (Beginning, Middle, Dilemma, Resolution, End), with a crew role picker,
a full script and guided read-through, three camera options per stage, a team
plan shared by code, a director's call sheet with 3-second timers, the set
rules (FRAME check, five-shot sequence, cut on movement, 180° rule) and a
review-and-improve step.

Served at **https://y6filmmaking.heutalab.com** by its own Cloudflare Worker,
separate from the main heutalab.com Worker so a classroom page can be
redeployed mid-unit without touching the site.

Framework-free: one HTML file, no build step. The only outside request is
Google Fonts (Big Shoulders Display, IBM Plex Sans).

```text
public/index.html   the whole page — markup, styles and behaviour
public/_headers     cache and security headers (Cloudflare reads this)
wrangler.jsonc      Worker + custom domain
```

## Addresses

The page routes by hash, so a class can be sent straight to one place:

| URL | Goes to |
|---|---|
| `/#/` | Film library |
| `/#/film/3/story` | Film 3's story overview (`script`, `plan`, `improve` work the same way) |
| `/#/film/3/beginning` | Film 3, stage 1 (`middle`, `dilemma`, `resolution`, `end`) |
| `/#/film/3/role` | Film 3's crew role picker |
| `/#/rules` | Set rules (`/#/rules/frame`, `/#/rules/r180` and so on jump to a section) |

## Where the work is kept

In the browser, on the device, in `localStorage` under keys starting `y6fp:`
(crew role, camera picks, prop ticks, review answers and notes). Nothing is
sent anywhere and there is no account. Teams share their camera plan between
devices with the team code on the Plan tab (for example `3-AB00C`).

## Deploy

```bash
npx --yes wrangler deploy
```

`npx wrangler login` once first, if the machine has not been used for this.
The custom domain in `wrangler.jsonc` creates the DNS record on first deploy.

## Preview locally

```bash
npx --yes wrangler dev --port 8749
```

## Provenance

Made in Codex and saved as `Y6_Film_Studio.html`
(Documents/Codex/2026-10-18), copied here unchanged on 18 October 2026.
`public/index.html` is the source of truth from here on.
