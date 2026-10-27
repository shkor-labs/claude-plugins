# Step 7. Read the numbers

Pull `ads_status` (per creative: impressions, 3-second views, CTR, live visits,
buy clicks, leads, spend) and `ads_who` (who clicked, which placements, how many
were real people).

Read the funnel top to bottom and stop at the first broken step:

| Step | Rough healthy range for a cold test | If it's below, change |
|---|---|---|
| 3-s view rate | > 25% | the first 2 seconds of the video |
| CTR | > 1% | the promise in the video / caption |
| Live visits / clicks | > 60% | page speed, mobile layout, the URL itself |
| Buy clicks / live visits | > 2% | headline, price anchor, proof on the page |
| Paid / buy clicks | > 20% | checkout friction, trust (legal, contact) |

These are starting points, not laws. With fewer than ~100 live visits, treat the
numbers as noise and say so.

Then compare against the kill criterion in `LAUNCH.md` and give the user one of
three decisions, with the reason:

- **Keep.** Funnel healthy, sales or strong buy-click rate. Scale the budget
  slowly, about ×2 per step.
- **Change one thing.** Fix the first broken step and rerun the same small test.
- **Kill or pivot.** Kill criterion hit twice. Return to step 1 with what
  `ads_who` revealed about who actually clicked.

`earnings` shows revenue that came in, the studio share withheld and the net
amount. Update `Status` in `LAUNCH.md`.
