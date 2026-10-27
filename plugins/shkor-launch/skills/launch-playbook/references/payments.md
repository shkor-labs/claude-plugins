# Step 4. Take money

0. **Check who will pay.** The checkout is Stripe, so it charges cards in USD
   through a US entity. If the buyers are mainly in a country where cards often
   fail on foreign merchants (Belarus and Russia, for example), say so before
   building the checkout. Confirm with one real test payment from a local card.
   If it fails, keep the free pilot or a "leave a request" flow for now, and
   file a `feature_request` for a local payment rail. Don't put a Buy button on
   the page that most of the audience can't use.
1. `product_create` with `name`, `price_usd` (0.5–20000) and `interval`
   (`month` | `year` | `week` | `day` | `one_time`). New products start in
   Stripe **test** mode and return a Payment Link.
2. Put the link behind the main call-to-action button. One button, one price,
   repeated at the top and bottom of the page.
3. **Test payment.** Open the link and pay with card `4242 4242 4242 4242`, any
   future date, any CVC. Check the success redirect and whatever the buyer is
   supposed to get after paying.
4. If the app must react to payments (unlock access, send a licence), register a
   webhook with `webhook_route_create`, giving the `target` URL of the
   back-end. The signing secret is shown **once**. Store it in the back-end's
   env and never in git or a front-end bundle. Verify the `Stripe-Signature`
   header in the handler. Events arrive only for this project. If you create
   Checkout Sessions in code instead of using the Payment Link, set
   `metadata.project_id`.
5. **Go live.** Live payments are switched on by the studio after a short
   review of the page, the legal pages from step 5, and the test payment. The
   user requests it in their account at https://shkor.com/account. Do step 5
   first so the review passes the first time. Once approved, `product_list`
   shows the live link. Put it on the page in place of the test link.

Money goes through the studio's Stripe account under the studio's legal entity.
The studio share agreed in step 2 is held automatically, and `earnings` shows
gross, withheld, net and what can be withdrawn.

Done when a test payment has gone through end to end and live payments are
requested (or already approved, with the live link on the page).
