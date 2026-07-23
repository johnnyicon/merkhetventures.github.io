# Cloudflare Pages migration checklist

## Objective

Move the public Merkhet Ventures website from GitHub Pages to Cloudflare Pages without changing email or disrupting the live website before the replacement is verified.

## What is ready in this repository

- Deployable static site: `apps/website/`
- Future experimental app: `apps/scroll-world/`
- Company, content, and brand source material: `content/` and `brand/`
- Legacy GitHub Pages implementation: `archive/legacy-titan-theme/`

## Current Cloudflare Pages deployment

The Git-connected Pages project is live and has been verified:

| Setting | Current value |
| --- | --- |
| Pages project | `merkhet-ventures` |
| Pages address | `https://merkhet-ventures.pages.dev` |
| Live custom domains | `https://merkhetventures.com` and `https://www.merkhetventures.com` |
| GitHub repository | `johnnyicon/merkhetventures.github.io` |
| Current Pages production branch | `codex/monorepo-cloudflare-pages` |
| Static output directory | `apps/website` |
| Build command | `exit 0` |
| First verified deployment | `970fe7f` |

The former four GitHub Pages apex A records have been replaced with a proxied Cloudflare Pages CNAME. The `www` record is also a proxied Cloudflare Pages CNAME. Google Workspace MX, TXT, CNAME, and SRV records remain unchanged.

## Ongoing publishing configuration

The site is intentionally running the approved migration branch for this initial cutover. Before normal ongoing publishing, merge the approved work into `master` and update the Pages production branch to `master`:

| Setting | Value |
| --- | --- |
| GitHub repository | `johnnyicon/merkhetventures.github.io` |
| Production branch | `master` after approval; the migration branch until then |
| Root directory | Repository root |
| Framework | None / static HTML |
| Build command | No build required (or `exit 0` if Cloudflare requests a command) |
| Build output | `apps/website` |
| Preview deployments | Enabled for non-production branches |
| Build watch paths | Include `apps/website/*`; exclude `archive/*` and, if desired, content-only paths |

Do not create a second project for Scroll World until that experiment has an approved build. It can later use the same repository with `apps/scroll-world` as its root directory.

## Completed cutover sequence

1. The approved migration branch was pushed and connected to Cloudflare Pages.
2. The generated `*.pages.dev` deployment was verified.
3. `merkhetventures.com` and `www.merkhetventures.com` were registered with the Pages project before changing DNS.
4. The four legacy GitHub Pages apex A records were retired and replaced with a proxied Pages CNAME; `www` now also points to Pages.
5. The apex site, `www`, HTTPS, and the hero image have all been verified live.
6. Google Workspace records were left unchanged.

Keep the old GitHub Pages source and configuration as a rollback reference until the new site has been stable and its ongoing publishing branch is switched to `master`.

## DNS records that must not change

Do not modify any Google Workspace or service DNS records during the website cutover, including:

- MX records
- Google verification TXT records
- Google service CNAME records
- XMPP or other service SRV records

Only the website-hosting records should change.

## Rollback

If the Cloudflare Pages domain fails after cutover, restore the prior four GitHub Pages A records from the archive/migration history. Do not alter email records.

## Important constraints

- A Cloudflare Pages custom domain must be added in the Pages dashboard before relying on a DNS record pointing to the Pages project.
- DNS and certificate activation may take several minutes after the custom domain is attached.
- The project will use Git integration. Cloudflare does not let a Git-integrated Pages project later switch to Direct Upload; that is acceptable here because GitHub remains the source of truth.
- Do not delete the legacy GitHub Pages archive until the new site is stable and the user explicitly approves permanent removal.
