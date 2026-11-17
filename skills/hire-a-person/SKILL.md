---
name: hire-a-person
description: Hire a real person through GoKuna to do something in the physical world and send a photo or video as proof. Use when the user needs a shelf price checked, a storefront or sign photographed, someone holding a sign, a voice line or short clip recorded, or any real-world proof an AI cannot get itself.
---

# Hire a person with GoKuna

Use the `gokuna` MCP tools. All money is in US cents (300 = $3.00).

## Before spending anything

1. Call `get_balance`. If it is short, tell the user the gap and offer `add_funds` (gives a card payment link the user pays themselves) or `redeem_code` if they have a `GK-XXXX-XXXX` code.
2. Work out the total: `rewardMinor x slots`. Say it in dollars, in one line: "This holds $9.00 (3 people x $3.00) from your GoKuna balance and you only pay for results you accept."
3. Wait for the user to confirm that amount. No confirmation, no `post_task`. A vague "sure" to a different plan is not confirmation.

## Write the brief

- `title`: 3-120 characters, the outcome ("Photo of the price tag on shelf X at store Y").
- `description`: what you need and why, in plain words.
- `kind`: `image` or `video`. `maxDurationSeconds` only for video (3-600).
- `instructions`: 1-20 short steps a stranger can follow with no context. Say what must be visible in the frame, from how far, in what light, and what makes it wrong.
- `rewardMinor`: minimum 300. Pay more for harder or longer tasks; low rewards sit untaken.
- `slots`: 1-500. One slot per independent result you need. Use 1 for a single fact, 3 when you want to cross-check.
- `countries`: two-letter codes to limit where, empty for anywhere.
- `idempotencyKey`: any unique string. Resending the same key returns the same task, so a retry never double-posts.

Not allowed: errands, deliveries, meeting someone, photos of other people, homes, schools, military or government sites. Decline those and say why.

## After posting

Give the user the task id and tell them results arrive over time. Use `get_task` for status and slots left, `list_tasks` for everything posted. Move on to the `review-results` skill when results come in.
