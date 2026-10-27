# Step 5. Legal pages

Stripe and Meta reject or freeze accounts that sell from pages without seller
details, terms and a refund policy. Payments go through the studio's US entity, so
the pages must name it as the seller.

1. `legal_entity` with `lang` (`en` | `ru`), `domain` (the site), and `purpose`
   (`footer`, `terms`, `privacy`, `refund` or `checkout`). It returns the public
   details and ready footer text/HTML, plus usage rules. Follow those rules.
2. Put the footer on every page.
3. Create `/terms`, `/privacy` and `/refund` pages and link them from the footer and
   next to the Buy button. Write them for **this** product: what is sold, how
   access is delivered, how to cancel, the refund window, and what data is
   collected (including the ads tracking snippet from step 6). Use plain language
   and keep it short.
4. Add a contact email the user actually reads.

Do not invent registration numbers, addresses or tax IDs. Use only what
`legal_entity` returns. Bank details and EIN are never published.

These pages are not legal advice. If the product touches health, finance, children or
regulated data, tell the user to get a lawyer's review before going live.
