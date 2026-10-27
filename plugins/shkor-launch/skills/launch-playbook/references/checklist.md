# Launch readiness checklist

Mark each item PASS / FAIL / N/A with a one-line reason. Any FAIL in the first two
groups blocks traffic.

## Must pass before ads
- [ ] `LAUNCH.md`: buyer, promise, one price, kill criterion filled
- [ ] Site opens over HTTPS at its public URL, on mobile, in < 3 s
- [ ] Promise from `LAUNCH.md` is visible without scrolling
- [ ] One Buy button → Stripe payment link (live, or live requested and test link working)
- [ ] A test payment succeeded end to end, including what the buyer gets after paying
- [ ] Footer with seller details from `legal_entity` on every page
- [ ] `/terms`, `/privacy`, `/refund` exist, are linked, and describe this product
- [ ] Working contact email

## Must pass for trust
- [ ] No fake testimonials, counts, logos; mockups labelled
- [ ] No secrets in the repo (`git log -p | grep -iE "sk_live|sk_test|agt_|api[_-]?key"` clean)
- [ ] No secret keys in the front-end bundle (only publishable keys)
- [ ] If on own server: app survives a reboot (systemd / pm2 / docker restart policy)
- [ ] Ads tracking snippet installed

## Nice to have
- [ ] 2–3 creatives testing different hooks
- [ ] Webhook handler verifies `Stripe-Signature`
- [ ] Open Graph title/image for link previews
