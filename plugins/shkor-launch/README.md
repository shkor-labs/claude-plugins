# shkor-launch

A Claude Code plugin from Shkor Labs that takes a product you built with AI from
"it works on my machine" to paying customers.

## What's inside

| Part | What it does |
|---|---|
| `launch-playbook` skill | Seven steps: offer → repo → public URL → payments → legal → first traffic → numbers |
| `shkor` MCP server | The infrastructure: private git, static hosting on `<slug>.cil.by` straight from your repo (no server needed), proxy to your own server, Stripe products and payment links, payment webhooks, legal entity details, Meta ads with fraud-filtered stats, earnings |
| `/launch` | Continue from the step you're on |
| `/launch-check` | Readiness review by an independent agent |
| `/launch-numbers` | Read the funnel and decide keep / change / kill |
| `launch-reviewer` agent | Checks the live site, checkout, legal and secrets |

## Install

```
/plugin marketplace add <marketplace-repo-url>
/plugin install shkor-launch@shkor
```

The playbook works without an account. The infrastructure steps need a Shkor
plan, which includes a cloud workspace server, the MCP and a monthly ad credit:
https://shkor.com/start

```
export SHKOR_TOKEN=agt_...   # add it to your shell profile, then restart Claude Code
```

Never commit the token.
