# Pricing

Credits are the single unit of purchase. One credit buys one **unit of work** — there are three kinds (see below).

| Pack | Price | |
| --- | --- | --- |
| Free tier | $0 | one credit per day per visitor (no account, no key) |
| Starter | $1.49 | 10 credits (≈15¢ each) |
| Studio | $5.99 | 50 credits (≈12¢ each) |

Buy at <https://narracore.app/checkout> — PayPal or credit/debit card (inside the PayPal window). The license key (`NRC-XXXX-XXXX-XXXX-XXXX`) is shown immediately after payment.

## What one credit covers

| Unit | Charged once per | Tools |
| --- | --- | --- |
| **Screenplay** — 24 hours | one screenplay (content fingerprint) | `format_screenplay`, `analyze_screenplay`, `diagnose_scenes`, `convert_fountain`, `build_video_prompts` |
| **Film analysis** — 24 hours | one `analysis_id` | `compile_film_breakdown` |
| **Story project** — 24 hours | one story project | `absorb_story_window` |

The three are independent: a credit spent on a screenplay is not a credit on a film analysis or a story project. Within one unit everything is bundled — send the same screenplay to `format_screenplay` and then to `analyze_screenplay` and you are charged once; recompile the same film analysis after re-observing with a different model and you are charged nothing.

These tools are always free: `check_video_prompts`, `get_film_contract`, `plan_film_analysis`, `validate_film_breakdown`, `prepare_story_window`, `render_story_handoff`, `check_credits` — plus `output="validate_only"` on the formatting tools and `material` mode on `diagnose_scenes`.

The free tier is one credit per day per visitor, and it can be spent on any of the three units.

## Rules (the honest version)

- **You pay for successful work only.** Rendering failures, validation failures and kernel errors are never charged.
- **Retries are free.** The same `request_id` never double-charges; a repeated call re-issues the result link.
- **Structure check is always free.** `output="validate_only"` costs nothing and never touches your quota.
- **Top-ups land on the same key.** Buy again with your key and credits simply add up.
- **Refunds:** within 7 days if unused — email huiyicd@foxmail.com with your order id.
- No subscription, no wallet, no auto-renewal. Unused credits don't expire.

## How the key is stored

We store only a SHA-256 hash of your key plus its last 4 characters for display. Lose the key? Email the address above with your order id.
