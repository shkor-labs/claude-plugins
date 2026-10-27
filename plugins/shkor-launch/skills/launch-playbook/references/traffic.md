# Step 6. First traffic

Goal: the first ~100 real visitors from strangers, enough to see whether the
offer is wanted. Friends and chats are biased, so paid traffic is the cleanest
test.

## Creatives

`ads_launch` takes up to 3 video URLs (mp4, 9:16 preferred, 5–90 s). Make each
one test a different **hook**, i.e. the first 2 seconds:

- the pain ("Still doing X by hand?")
- the outcome ("X done in 30 seconds")
- the proof (a screen recording of the product doing the thing)

Show the real product. No fake UI and no stock "happy people".

## Launch

1. Run the readiness check first: `launch-reviewer` agent or `checklist.md`.
2. Install the `tracking_snippet` from `ads_status` on every page. Without it
   there's no live-visit or buy-click data in step 7.
3. Propose a budget and **wait for an explicit yes**. A first test of
   $5/day × 2 days or $10 × 1 day is enough. The plan includes a monthly ad
   credit that is spent first and expires at the end of the month.
4. `ads_launch`. The studio checks the ad against Meta rules. If the budget
   exceeds the credit, a payment link appears in `ads_status`. The studio then
   approves and the campaign starts. Relay any reviewer remarks to the user.
5. To stop, use `ads_pause` with `id`. To continue, use `ads_pause` with
   `resume: true`.

Free channels to run in parallel: a post in 2–3 communities where the buyer
from `LAUNCH.md` hangs out, written as a story of the problem, not as an ad.
