# Merkhet Ventures — Repository Reorganization Plan

**Status:** Working plan for review
**Purpose:** Turn the current GitHub Pages repository into a clean monorepo for the Merkhet Ventures website, content, and future interactive experiments—without risking the live site during the transition.

## Decision

Merkhet Ventures should remain in **one repository**. A second repository is not necessary.

The repository should become a small monorepo with clear boundaries between:

1. the current/public website;
2. future website experiences, including a possible Scroll World build;
3. the strategic and brand source material that informs those experiences; and
4. the legacy theme files retained temporarily for reference.

A new Codex session can work safely in the same repository. The key is not isolation by repository; it is a clear written brief, a designated build folder, and explicit instructions about which files are authoritative and which folders must be ignored.

## Current audit

### What the live site uses today

The live GitHub Pages site is currently a single static homepage built around `index.html` and the custom domain declaration in `CNAME`.

`index.html` directly uses:

- `assets/images/section-10.jpg` — current hero image
- `assets/images/testimonial_bg.jpg` — Lao Tzu quote background
- Bootstrap, jQuery, Flexslider, and the existing theme’s CSS/JavaScript assets
- Google-hosted fonts

`404.html` is also live-capable and has its own generic theme dependencies, including `assets/images/section-4.jpg` and favicon assets.

The current website does **not** directly link to the old PHP forms or the large collection of template demo pages.

### What is legacy material

The repository contains approximately **120 legacy HTML example pages**, covering portfolios, shops, restaurants, galleries, blogs, services, pricing, and UI components. These are generic theme samples rather than Merkhet Ventures content.

It also contains extensive legacy theme material:

- about 29 MB of `assets/` within a 52 MB repository
- hundreds of gallery, shop, restaurant, portfolio, and demonstration images
- theme source SCSS, vendor libraries, and demo assets
- PHP contact, reservation, newsletter, and request-call endpoints

The PHP files cannot operate on GitHub Pages, which is static hosting. They are not connected to the live homepage or 404 page.

### Material created for the new direction

These files are meaningful source material and should be retained:

- `concept.html` — the separate visual/content concept, not live
- `content-discovery-interview.md` — interview guide and working notes
- `content-discovery-transcript.jsonl` — verbatim discovery record
- `merkhet-ventures-content-strategy.md` — website positioning and architecture
- `merkhet-ventures-company-profile.md` — primary company narrative
- `merkhet-ventures-company-profile.html` — presentable profile version

## Recommended target structure

```text
merkhetventures.github.io/
├── apps/
│   ├── website/                     # Current or next public Merkhet site
│   │   ├── index.html
│   │   ├── 404.html
│   │   └── assets/
│   └── scroll-world/                # Separate experimental build; never edits website directly
│       ├── brief.md
│       ├── index.html
│       ├── assets/
│       └── generated-media/
├── content/
│   ├── company-profile.md           # Primary narrative source of truth
│   ├── website-content-strategy.md
│   ├── discovery-interview.md
│   └── discovery-transcript.jsonl
├── brand/
│   ├── brand-brief.md               # Visual and tonal guidance
│   └── reference-images/
│       └── section-10.jpg
├── plans/
│   └── repo-reorganization-plan.md
├── archive/
│   └── legacy-titan-theme/          # Temporary holding area for old template material
├── README.md
└── AGENTS.md                         # Instructions for future Codex sessions
```

The names can be refined later. The important distinction is that `apps/website/` is the public site, `apps/scroll-world/` is an isolated experiment, and `content/` plus `brand/` are the source material for both.

## Recommended reorganization sequence

### Phase 1 — Preserve and prepare

1. Commit the current discovery/profile work.
2. Add this plan and a short root `README.md` explaining the repository’s purpose.
3. Create the new folder structure without moving or deleting public files yet.
4. Create a concise `brand/brand-brief.md` and, later, a `apps/scroll-world/brief.md`.

At this point, the live site remains completely unchanged.

### Phase 2 — Archive the legacy theme

Move the generic theme demos, unused images, SCSS source, PHP endpoints, and vendor material into `archive/legacy-titan-theme/` as a single preservation step. Do not attempt a piecemeal dependency cleanup while the current `index.html` still runs on the old theme.

Keep the following in place until a replacement public site is ready:

- `index.html`
- `404.html`
- `CNAME`
- every asset directly referenced by those two pages

This archive step makes the active surface obvious while preserving a recoverable copy of everything else.

### Phase 3 — Establish the new public website

Build the approved replacement inside `apps/website/`. The replacement should be self-contained and should not depend on the legacy theme.

When it is ready, connect `apps/website/` to a Cloudflare Pages project. Cloudflare Pages supports a project root directory inside a monorepo, so the public site does not need to live at the repository root.

The custom domain should remain on GitHub Pages until the Cloudflare Pages preview is approved. At cutover, replace only the website-hosting records with the Cloudflare Pages records. Google Workspace records remain unchanged.

### Phase 4 — Decide what to delete

After the replacement website is live and verified, decide whether to:

- retain `archive/legacy-titan-theme/` in Git for historical reference; or
- remove it in one deliberate commit.

Deletion should happen only after the old site has been replaced and the archive has been reviewed. There is no need to carry the legacy template indefinitely, but there is also no reason to delete it before the new deployment is proven.

## Cold-start instructions for a future Scroll World session

The new session should work only inside `apps/scroll-world/` and should not modify the public website. Give it this instruction:

> Build a separate Scroll World concept for Merkhet Ventures. Read only the following sources before making design decisions: `content/company-profile.md`, `content/website-content-strategy.md`, `brand/brand-brief.md`, and `apps/scroll-world/brief.md`. Use `brand/reference-images/section-10.jpg` only as a visual reference if useful. Do not read or reuse anything in `archive/`. Do not modify `apps/website/`, deployment settings, DNS, or the live site. Create all output inside `apps/scroll-world/`.

### Files to provide to the skill

**Required**

1. `content/company-profile.md` — the primary narrative and positioning source.
2. `content/website-content-strategy.md` — prevents false claims such as a current fund, team, portfolio, or generic agency positioning.
3. `brand/brand-brief.md` — visual tone, palette, typography preferences, and boundaries.
4. `apps/scroll-world/brief.md` — the specific story that the camera should tell.

**Optional**

- `content/discovery-transcript.jsonl` — use only when more nuance is needed; it is not a primary creative brief.
- `concept.html` — visual reference only, not a source of truth for the final architecture.
- `brand/reference-images/section-10.jpg` — reference image only.

**Do not provide as creative source material**

- `index.html`
- old template pages
- old PHP files
- legacy `assets/` folders

Those files would over-weight the old theme and dilute the Merkhet direction.

## Scroll World: initial scope

The first experiment should be a three-scene, desktop-only proof of concept. It should not replace the main website or require native mobile video on the first run.

| Scene | Narrative role | Possible world metaphor |
| --- | --- | --- |
| **Clarity** | Knowledge becoming wisdom | A quiet architectural space opening around a seed or source of light. |
| **Community** | Connection, capability, and shared agency | Interlinked homes, civic spaces, local enterprise, and shared movement. |
| **Harmony** | Systems, environment, and responsible transition | Community infrastructure and landscape operating in balance. |

The desired tone is architectural, contemplative, and credible—not playful for its own sake, overly literal, or styled like a generic AI product launch.

## Brand brief: why it matters

The Scroll World skill interviews for a brand kit and art direction. A brand brief will not prevent good creative exploration; it gives that exploration meaningful boundaries.

For Merkhet, the brief should preserve:

- the reflective, serious, quietly optimistic tone
- the original teal-to-earth gradient as a reference point
- generous space, architectural imagery, and editorial typography
- the language of knowledge, wisdom, impact, communities, systems, and harmony

It should explicitly avoid:

- generic AI agency aesthetics
- fake portfolios, fake teams, or fake scale
- cartoonish or game-like impact imagery
- activist, government-contractor, or capital-only fund positioning

## Hosting consideration for a future Scroll World

GitHub Pages is suitable for a small proof of concept. A public video-led experience with meaningful traffic should eventually serve generated media from Cloudflare-backed storage or a CDN, while the website remains deployable from this monorepo.

## Decisions before implementation

1. Approve the target folder structure.
2. Decide whether the legacy theme should be archived in Git or removed after replacement.
3. Create the brand brief before inviting the Scroll World skill into a new session.
4. Write and approve the three-scene Scroll World brief.
5. Set a Higgsfield budget and choose whether the proof of concept remains desktop-only.
