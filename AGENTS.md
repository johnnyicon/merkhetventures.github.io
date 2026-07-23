# Merkhet Ventures repository guide

## Purpose

This is a monorepo. Treat each application and its source material as deliberately separate.

## Authoritative context

Before making strategic, brand, or website decisions, read:

1. `content/company-profile.md`
2. `content/website-content-strategy.md`
3. `brand/brand-brief.md`

Use `content/discovery-transcript.jsonl` only when additional nuance is needed. It is a verbatim source record, not a concise creative brief.

## Application boundaries

- Make public-site changes only inside `apps/website/`.
- Make Scroll World experiment changes only inside `apps/scroll-world/`.
- Do not modify one application while working on the other unless the user explicitly asks.
- Do not treat files in `archive/` as design or implementation input. They are historical material only.

## Hosting and domain safety

- Do not change DNS, custom domains, Cloudflare Pages settings, or deployment targets without explicit user approval.
- Google Workspace DNS records are out of scope for website changes and must remain intact.
- The deployed site must be a static build with an `index.html` at the deployed output root.

## Scroll World cold start

When asked to build the Scroll World concept, read `apps/scroll-world/brief.md` plus the three authoritative context files above. Do not read the archived theme or modify `apps/website/`.
