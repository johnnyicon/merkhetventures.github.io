# Higgsfield and Scroll World Cost Analysis

Updated: 2026-07-23

## Executive summary

For the first Merkhet World build, Higgsfield is probably the better-value path in practical terms. Direct provider APIs can have lower raw generation costs, but they require separate accounts, billing, authentication, model access, retries, frame-locking, downloads, and assembly. Higgsfield bundles those models and the creative workflow into one place.

The Twitter example reported five frame-locked 1080p scenes, desktop and mobile verification, and 467 Higgsfield credits spent out of 500. That is consistent with the Scroll World skill's expected first-build range.

The important qualification is that Plus and Ultra are not identical:

- Plus: 1,200 credits/month; the displayed Seedance 2.0 unlimited mode is 720p/15 seconds.
- Ultra: 3,000 credits/month; the displayed Seedance 2.0 unlimited mode includes 1080p/8 seconds.

Therefore, Plus is likely enough for a 720p proof of concept. Ultra is the closer match to the Twitter example's 1080p result, even though we probably do not need all 3,000 credits.

## Two different kinds of usage

The Twitter screenshot shows:

- **467 Higgsfield credits:** media-generation usage.
- **766,562 agent tokens:** the coding agent's work while building the site.

These are separate accounting systems. Agent tokens are not Higgsfield credits.

## Providers represented in Higgsfield

| Higgsfield label | Underlying provider | Direct route |
| --- | --- | --- |
| Seedance 2.0, Fast, Mini | ByteDance | BytePlus ModelArk or Dreamina |
| Seedream 5.0 Pro | ByteDance | BytePlus/Dreamina |
| Nano Banana Pro, Nano Banana 2 | Google | Gemini API, Google AI Studio, or Gemini app |
| Gemini Omni Flash | Google | Gemini API or Gemini app |
| Kling 3.0 | Kuaishou | Kling AI |
| GPT Image 2 | OpenAI | OpenAI API or ChatGPT Images |
| Wan 2.7 | Alibaba | Alibaba Cloud Model Studio |
| Eleven v3 | ElevenLabs | ElevenLabs API or app |
| MiniMax Speech | MiniMax | MiniMax/Hailuo APIs |
| VibeVoice | Microsoft/research ecosystem | Direct/open-source route |

Existing subscriptions do not automatically transfer into Higgsfield. A Google subscription may provide access in Google's own products; a ChatGPT subscription and OpenAI API billing are separate; and an ElevenLabs subscription can cover Eleven v3 directly, but not necessarily the same model invoked inside Higgsfield.

## Estimated first-build costs

Assumptions: five scenes, 1080p video, approximately 10-second scene legs, 5-second connectors, and roughly 15% retry headroom.

| Approach | Approximate media cost | Notes |
| --- | ---: | --- |
| Higgsfield, desktop continuous-forward build | 300–480 credits | Comparable to the 467-credit example |
| Higgsfield, native desktop + mobile video | 600–900 credits | Mobile requires an additional portrait chain |
| Direct BytePlus-style 1080p video, desktop | $30–$45 | Raw generation estimate; excludes engineering and account setup |
| Direct BytePlus-style 1080p video, desktop + mobile | $60–$90 | Depends on duration, retries, and regional pricing |
| Direct dive-and-connector build with mobile | $80–$120 | More video generations and more seam-sensitive retries |
| Direct still-image generation | Usually under $1 for five stills | Google and OpenAI API image costs are small relative to video |

Direct APIs can therefore be cheaper on raw generation alone. They are not automatically cheaper for this project overall because the Scroll World workflow depends on frame-locked seams, sequential continuation, asset extraction, retry handling, and final web assembly. Higgsfield's value is the bundled access and workflow, not merely the price of a single generation.

## Recommendation

Use Higgsfield for the first build. Choose Plus if a 720p proof of concept is acceptable. Choose Ultra only if we want a close reproduction of the Twitter example's 1080p Seedance output. Do not buy Ultra solely for the 3,000-credit balance.

Before spending, run one still and one video, compare the balance before and after, and then extrapolate. Also confirm whether the Higgsfield CLI workflow consumes credits even when the web plan advertises unlimited access.

## Sources

- [Higgsfield unlimited-plan explanation](https://geo.higgsfield.ai/task/blog/higgsfield-unlimited-plan-change)
- [Google Gemini API pricing](https://ai.google.dev/gemini-api/docs/pricing)
- [Google AI plan pricing](https://one.google.com/about/plans)
- [OpenAI GPT Image 2 model](https://developers.openai.com/api/docs/models/gpt-image-2)
- [OpenAI ChatGPT/API billing separation](https://help.openai.com/en/articles/8156019)
- [ElevenLabs API pricing](https://elevenlabs.io/pricing/api?price.platform=api)
- [BytePlus Seedance pricing](https://docs.byteplus.com/docs/Dramagic/PlansPackages)
- [Alibaba Wan pricing](https://www.alibabacloud.com/help/en/model-studio/model-pricing)
