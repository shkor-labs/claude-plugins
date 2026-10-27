---
name: launch-playbook
description: Take a product the user built (often vibe-coded) from "it runs on my machine" to paying customers. Use when the user wants to launch, ship, go live, publish, deploy for real users, take payments, add pricing, a checkout or Stripe, add legal pages (terms, privacy, refund), get first users, run ads, or asks "what do I do now that it works?" / "how do I sell this?". Also use when checking launch readiness or reading post-launch numbers.
---

# Launch playbook

Most vibe-coded products die between "it works" and "someone paid". The code is
rarely the blocker. What's missing is a public URL, a price, a checkout, legal
pages, and a first stream of real visitors. This playbook walks the user through
those steps in order. The `shkor` MCP server does the parts that need
infrastructure.

Talk to the user in their language. Keep each step small and finish it before
starting the next. A launched rough product beats a polished unlaunched one.

## Before anything: is the MCP connected?

Call the `whoami` tool of the `shkor` server.

- **It works.** Note the project and plan it reports, then continue.
- **401 / unauthorized / tool missing.** Stop and tell the user that the
  infrastructure steps need a Shkor token. They get one with a plan at
  https://shkor.com/start, then run `export SHKOR_TOKEN=agt_...` (or put it in
  their shell profile) and restart Claude Code. Steps 1 and 7 still work without
  a token, so offer to do those meanwhile.

Never ask the user to paste the token into the chat. Never print it, commit it,
or write it into project files.

## The seven steps

| # | Step | Done when | Tools | Details |
|---|------|-----------|-------|---------|
| 1 | Frame the offer | one-line promise, one buyer, one price | none | `references/offer.md` |
| 2 | Project + repo | project exists, code pushed to private repo | `project_create`, `git_repo_create` | `references/ship.md` |
| 3 | Public URL | `https://<slug>.cil.by` opens over HTTPS | `site_publish` (static) or `site_request` (own server) | `references/ship.md` |
| 4 | Take money | test payment passed, live payments requested | `product_create`, `product_list`, `webhook_route_create` | `references/payments.md` |
| 5 | Legal | footer with seller details, terms/privacy/refund pages | `legal_entity` | `references/legal.md` |
| 6 | First traffic | ads campaign approved and spending, tracking snippet on site | `ads_launch`, `ads_status` | `references/traffic.md` |
| 7 | Read the numbers | decision: keep / change offer / kill | `ads_status`, `ads_who`, `earnings` | `references/numbers.md` |

Read only the reference for the step you are on.

## Rules

- **Find the current step first.** Ask or check what already exists
  (`product_list`, `git_repo_list`, a site that already opens) before creating
  anything. Don't create duplicate projects, repos or products.
- **Test mode first, then live.** Products start in Stripe `test`. Live
  payments are switched on by the studio after a review, which the user
  requests in their account at https://shkor.com/account. Don't try to switch
  modes yourself.
- **Spending money needs an explicit yes.** That covers `ads_launch` and
  anything else that charges the user. Show the amount and the duration, then
  wait for the answer.
- **One price.** One product, one price in USD. No tiers, coupons or "early
  bird" variants until the first sale (step 1 explains why).
- **Be honest on the page.** No fake testimonials, user counts or "as seen in"
  logos. Label mockups as mockups.
- **Missing capability.** If something the user needs isn't covered by the
  tools, do it by hand and also file it with `feature_request`. Call
  `feature_backlog` first so you don't file a duplicate.

## Readiness check

When the user asks "am I ready?" or before step 6, run the `launch-reviewer`
agent, or walk `references/checklist.md` yourself.
