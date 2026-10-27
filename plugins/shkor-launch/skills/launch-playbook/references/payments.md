# Step 4. Take money

1. `product_create` with `name`, `price_usd` (0.5–20000), `interval`
   (`month` | `year` | `week` | `day` | `one_time`) and `mode: "test"`. It returns a
   Stripe Payment Link.
2. Put the link behind the main call-to-action button. One button, one price,
   repeated at the top and bottom of the page.
3. **Test payment.** Open the test link and pay with card `4242 4242 4242 4242`,
   any future date, any CVC. Check that the success redirect works.
4. If the app must react to payments (unlock access, send a licence), register a
   webhook with `webhook_route_create`, giving the `target` URL on the user's
   server. The signing secret is shown **once**. Store it in the server's env and
   never in git. Verify the `Stripe-Signature` header in the handler. Events
   arrive only for this project. If you create Checkout Sessions in code instead
   of using the Payment Link, set `metadata.project_id`.
5. Only after the test passes and the user says yes: `product_set_mode` with
   `mode: "live"`, and replace the link on the page with the live one
   (`product_list` shows both).

Money goes through the studio's Stripe account under the studio's legal entity (see
step 5). The studio share is held automatically, and `earnings` shows gross,
withheld, net and what can be withdrawn.

Done when the live link is on the page and the user has seen a successful test payment.
