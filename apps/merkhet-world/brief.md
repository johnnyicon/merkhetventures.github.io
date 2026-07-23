# Merkhet World — Cold-start prompt

Copy the prompt below into a fresh agent session after the `scroll-world` skill is installed and Higgsfield has been authenticated.

```text
Use the installed `$scroll-world` skill to create a separate, desktop-first proof of concept called “Merkhet World.”

First, read these files in this exact order:

1. AGENTS.md
2. content/company-profile.md
3. content/website-content-strategy.md
4. brand/brand-brief.md
5. apps/website/index.html

Treat files 2–4 as the authoritative source for meaning, positioning, language, and visual boundaries. Use file 5 only as a reference for the approved public-site tone, hero image, and teal-to-earth gradient. Do not modify it.

Subject: Merkhet Ventures — a holding and venture company for strategy, partnerships, and practical work across communities, systems, and technology. The world should make its point of view tangible: change begins with clearer understanding, grows through connection and community capability, and must ultimately strengthen people, communities, and the environment.

Scope and boundaries:

- Build only inside apps/merkhet-world/. Do not alter apps/website/, content/, brand/, archive/, Cloudflare configuration, DNS, or the live website.
- This is an exploratory proof of concept, not a replacement for the current public site.
- Do not use archived files as design or content input.
- Do not invent a portfolio, fund, team, clients, investment activity, or impact claims.

Create one continuous, scroll-scrubbed camera journey through three connected scenes:

1. Clarity — knowledge becoming wisdom; change begins with the individual.
2. Community — connection, capability, shared agency, and local action.
3. Harmony — systems, environment, responsible transition, and long-term balance.

Use the skill’s miniature/diorama “dive-in plus aerial connector” architecture for this concept. Each scene should begin as a coherent, high-level world and allow the camera to descend into a meaningful interior or focal moment. The aerial transitions should feel like moving through one connected world, not like cuts between unrelated illustrations. Use one frame-locking video model for the entire chain.

Use this shared visual register unless the source material gives you a compelling reason to propose a small refinement: soft matte low-poly clay diorama, isometric miniature architecture, tilt-shift depth, warm directional light, restrained material texture, thoughtful and spacious composition. Keep the world materially grounded and slightly poetic, never cute or game-like.

The world should feel architectural, contemplative, materially grounded, credible, and quietly ambitious. Make it reflective rather than promotional. It must not look like a generic AI launch, videogame, cartoon, activist campaign, fake venture portfolio, or literal stock-photo philanthropy.

Keep the public-facing message restrained: “Transforming Knowledge Into Wisdom For Impact.” The Lao Tzu quote is an optional philosophical anchor, not copy that needs to appear in full. The goal is to make Merkhet’s point of view tangible, not to explain every part of the company profile.

Start with a desktop-only concept. Do not generate a native mobile video chain unless I explicitly approve it.

Before generating any paid Higgsfield image or video assets:

1. Propose the three scene descriptions, visual treatment, and a concise narrative transition for each seam.
2. State the exact proposed asset count, including stills, camera clips, connector clips, and any mobile assets.
3. Show the available Higgsfield balance and give an estimated credit range or explain precisely what cannot be estimated.
4. Stop and wait for my explicit budget approval.

After approval, create the implementation only in apps/merkhet-world/. Use the skill’s seam-safe pipeline and portable scroll engine. Include a still-image/reduced-motion fallback, semantic HTML, keyboard-accessible controls, and no auto-playing audio. Keep assets optimized and lazy-loaded.

Before finishing, test the desktop experience locally, review it against the source material above, correct obvious reading, performance, and seam issues, and give me the local preview URL plus a short list of the files created.
```

## Prerequisites

The full Scroll World pipeline needs:

1. The `scroll-world` skill installed for the agent that will build it.
2. Higgsfield CLI installed, authenticated, and funded for the image-to-video camera flights.
3. `ffmpeg` and `ffprobe` available locally.
4. Python 3 with Pillow available locally.

Codex image generation can optionally provide the scene stills, but Higgsfield is still needed for the frame-locked video flights that make this a Scroll World.

## Helpful but not required

- The source hero image is `apps/website/assets/images/section-10.jpg`. It may be used as a tonal reference; do not assume it should appear in the 3D world.
- `content/discovery-transcript.jsonl` is available if genuinely needed for nuance, but do not load it by default.
