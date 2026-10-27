# Step 7. Read the numbers

Pull `ads_status` (per creative: impressions, 3-second views, CTR, live visits,
buy clicks, leads, spend) and `ads_who` (who clicked, which placements, how many
were real people).

## First: is there enough data?

| Question | Minimum before you judge it |
|---|---|
| Which creative is best | ~250 impressions per creative |
| Does the page hold people | ~30 live visits |
| Do people want to buy | ~100 live visits |

Below the minimum, say "not enough data yet". Don't pick a winner or kill the
offer on 10 visits.

## Then: read the funnel top to bottom and stop at the first broken step

| Step | Weak | OK | Good | If weak, change |
|---|---|---|---|---|
| 3-s views / impressions | < 12% | 15–25% | > 25% | the first 2 seconds of the video |
| Link CTR | < 0.8% | 1–2% | > 2% | the promise in the video and caption |
| Live visits / link clicks | < 45% | 50–70% | > 70% | page load speed on mobile, redirects |
| Buy clicks / live visits | < 1% | 2–5% | > 5% | headline, proof, price anchor |
| Paid / buy clicks | < 10% | 20–40% | > 40% | checkout friction, trust (legal, contact) |

Calibration: the studio's first cold test (October 2026, 3 creatives, $15) got
13–21% 3-s views, 1.2–3.0% link CTR and 56–67% landing views per link click.
The thresholds will move as more campaigns come in.

## Decide

Compare against the kill criterion in `LAUNCH.md` and give the user one of three
decisions, with the reason:

- **Keep.** Funnel OK or good all the way down, or there are sales. Raise the
  budget about ×2 per step and keep only the winning creative.
- **Change one thing.** Fix the first weak step and rerun the same small test.
  Change one thing per run, or you won't know what worked.
- **Kill or pivot.** Kill criterion hit on enough data. Return to step 1 with
  what `ads_who` showed about who actually clicked, which is often a different
  buyer than planned.

`earnings` shows revenue that came in, the studio share withheld and the net
amount. Update `Status` in `LAUNCH.md`.
