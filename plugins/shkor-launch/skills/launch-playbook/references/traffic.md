# Step 6. First traffic

Paid traffic is the cleanest test because friends and chats are biased. But be
clear with the user about what each budget can answer.

| Budget | Roughly buys* | What it can tell you |
|---|---|---|
| $10–15 | ~800 impressions, ~10 visits | Which video hook stops the scroll (3-s views, CTR). Nothing about sales. |
| $50–80 | ~40–60 visits | Whether the page holds people. A first, noisy read on buy clicks. |
| $150+ | ~100+ visits | Buy-click rate you can act on. |

\* From the studio's first cold test in October 2026: about $0.65 per link click
and $1.40 per landing view. Niche, country and creative move these a lot.

So the first test is a **creative test**. Run the conversion test only after a
creative has won.

## Creatives

`ads_launch` takes up to 3 video URLs (mp4, 9:16 preferred, 5–90 s). Make each
one test a different **hook**, i.e. the first 2 seconds:

- the pain ("Still doing X by hand?")
- the outcome ("X done in 30 seconds")
- the proof (a screen recording of the product doing the thing)

Show the real product. No fake UI and no stock "happy people". Put the promise
as on-screen text, because most people watch with the sound off.

## Launch

1. Run the readiness check first: `launch-reviewer` agent or `checklist.md`.
2. Install the `tracking_snippet` from `ads_status` on every page. Without it
   there's no live-visit or buy-click data in step 7.
3. Propose a budget using the table above and **wait for an explicit yes**. The
   plan's monthly ad credit is spent first and expires at the end of the month,
   so it's the natural creative test ($5/day × 2 days or $10 × 1 day).
4. `ads_launch`. The studio checks the ad against Meta rules. If the budget
   exceeds the credit, a payment link appears in `ads_status`. The studio then
   approves and the campaign starts. Relay any reviewer remarks to the user.
5. To stop, use `ads_pause` with `id`. To continue, use `ads_pause` with
   `resume: true`.

Free channels to run in parallel: a post in 2–3 communities where the buyer
from `LAUNCH.md` hangs out, written as a story of the problem, not as an ad.
These posts often bring the first buyers before ads do.
