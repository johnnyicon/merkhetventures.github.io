# Cloudflare Pages migration checklist

## Objective

Move the public Merkhet Ventures website from GitHub Pages to Cloudflare Pages without changing email or disrupting the live website before the replacement is verified.

## What is ready in this repository

- Deployable static site: `apps/website/`
- Future experimental app: `apps/scroll-world/`
- Company, content, and brand source material: `content/` and `brand/`
- Legacy GitHub Pages implementation: `archive/legacy-titan-theme/`

## Cloudflare Pages project configuration

Create one Git-connected Cloudflare Pages project for the public website:

| Setting | Value |
| --- | --- |
| GitHub repository | `johnnyicon/merkhetventures.github.io` |
| Production branch | `master` |
| Root directory | `apps/website` |
| Framework | None / static HTML |
| Build command | No build required (or `exit 0` if Cloudflare requests a command) |
| Build output | The directory containing `index.html` |
| Preview deployments | Enabled for non-production branches |
| Build watch paths | Include `apps/website/*`; exclude `archive/*` and, if desired, content-only paths |

Do not create a second project for Scroll World until that experiment has an approved build. It can later use the same repository with `apps/scroll-world` as its root directory.

## Safe cutover sequence

1. Push the approved migration branch and connect the repository to Cloudflare Pages.
2. Verify the generated `*.pages.dev` preview thoroughly.
3. Confirm `merkhetventures.com` and `www.merkhetventures.com` are not yet attached to the Pages project.
4. At the approved cutover moment, add the custom domain in the Cloudflare Pages project before changing DNS. The domain is already an active Cloudflare zone, so no nameserver change is needed.
5. Follow Cloudflare's generated DNS instructions: retire only the four legacy GitHub Pages apex A records and the legacy `www` website record, then use the proxied Cloudflare Pages records.
6. Verify the apex site, `www` behavior, HTTPS certificate, and the 404 page.
7. Only after the Cloudflare Pages domain is active, remove the custom domain from GitHub Pages. Keep the old GitHub Pages source archived for rollback until the new site has been stable.

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
