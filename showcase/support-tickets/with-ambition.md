## Ambition ladder: Q3 support tickets for the quarterly review

**Rung 0 · As asked:** 5–6 slides summarizing ~4,200 Q3 Zendesk tickets (volume, priority, status, CSAT, plan mix) for the review next Thursday, Nov 5. You have the CSV, including the full text of every ticket. It doesn't have resolution times, account IDs or revenue.
**Best axes:** Altitude + Depth. The deck feeds a meeting that decides where Q4 effort goes, and what customers actually wrote is a far better source than tags agents added in a hurry. Range adds one move: a fresh reviewer tries to break each headline claim before your manager sees it (built into the prompt below).

### Rung 1 · Stretch — Depth
Same slides, built from the ticket text instead of the tags. Sort all 4,200 descriptions into 15–25 root causes, show what changed since Q2 and why, and point out where the tags were misleading.
Judged by: you label 100 random tickets yourself without seeing the AI's labels, and the two agree on at least 80%.

### Rung 2 · Bold — Altitude ← recommended
Turn the review from a status report into three decisions. Find no more than three fixable root causes that together drove at least 30% of Q3 tickets. For each one, show its volume vs Q2, how much CSAT it costs (using a model that separates the effect of the issue from the effect of the customer's plan and the ticket's priority), its share of top-plan accounts, a named owner team, and a fix that could ship in Q4. End with a written prediction you'll check at next quarter's review: "each of these falls 40% or more within six weeks of its fix shipping."
Needs: Q3 CSV, Q2 export, Python with DuckDB + scikit-learn · Judged by: the 100-ticket blind check, ticket and CSAT totals matching Zendesk's own Q3 report within 1%, and Q4's real ticket counts against the prediction

### Rung 3 · Audacious — Altitude
Replace the quarterly ticket recap with a Monday root-cause watch. It pulls new tickets from the Zendesk API, sorts them with the same classifier, and pings the owner team when a cause jumps outside its normal week-to-week range. Test it on Q3 history first, then run it alongside the Q4 deck. · Judged by: how many weeks of warning it would have given on Q3's biggest spike; your support lead confirms at least 70% of its Q4 alerts as real

**Recommended: Rung 2.** It still fits in 5–6 slides and takes about two days of agent work plus an hour of yours. It hands the room decisions instead of a status report, and it builds the classifier Rung 3 needs.
**Unlocks:** Q3 CSV (have) · Q2 export, same columns (set up: 5 min in Zendesk) · Python + DuckDB + scikit-learn (set up: minutes) · OK under your company's data policy to send ticket text to an AI tool (set up) · a heads-up to your manager by Monday that the deck makes recommendations, and 15 minutes with each owner team before their name goes on a slide (set up)
**Trust risks:** Counts that don't match the Zendesk dashboard people already trust → reconcile with it first and footnote the match. Customer names and emails inside descriptions → strip them out before any text leaves your machine.
**Cheap path:** Zendesk Explore's standard reports produce the Rung 0 charts in about 10 minutes. Use those for the appendix and put your time into root causes.

**What it would look like** (sketch, made-up numbers):
```text
Slide 1 · Three fixes would have prevented 1 in 3 Q3 tickets
4,212 tickets (+18% vs Q2) · CSAT 81% (down 6 pts) · 24% of tickets rated

Root cause (from ticket text)        Tickets  CSAT  Enterprise  Owner     Ask for Q4
SSO login loop since Aug 12 release      612   58%     41%      Platform  Fix redirect by Nov 30
Invoice PDF missing PO number            388   64%     67%      Billing   Add PO field
CSV import fails silently >10k rows      301   71%     22%      Data      Real error message + docs
Together: 1,301 tickets (31%), explaining 4.1 of the 6-point CSAT drop
46% of the SSO tickets were tagged "how-to". The text says they're bugs.
Prediction to check next quarter: each cause down 40%+ within 6 weeks of its fix.
```

**Upgraded prompt** (paste this):
```text
Goal: our quarterly review is Thursday Nov 5. The real outcome is a Q4 decision on which support problems
product, billing and docs fix first. Build the analysis behind a 5-6 slide deck that makes three
recommendations, not a status summary. Show me findings and a slide outline first; no slides until I approve.

Inputs: zendesk_q3.csv (~4,200 rows: id, created_at, subject, description, tags, priority, status,
satisfaction_rating, account_plan), zendesk_q2.csv (same columns), and Q3 totals from Zendesk Explore: <paste>.

Method:
1. Load into DuckDB. Check duplicate ids, created_at within 2026-07-01..09-30, and satisfaction_rating
   variants (good/bad/offered/unoffered, with-comment forms). Reconcile ticket count and CSAT to the Explore
   totals within 1% before anything else; explain any gap.
2. Redact emails, phone numbers and personal names from subject/description before any text reaches a model.
3. Draft a root-cause codebook (15-25 codes + "other") from embeddings + clustering on a 300-ticket sample,
   then label every ticket with an LLM classifier using that codebook. Label from text, not tags; afterwards,
   report where tags and text disagree.
4. Per code: Q2 vs Q3 volume, weekly trend, CSAT on rated tickets with response rate and Wilson 95% CI,
   priority and plan mix. Fit logistic regression bad_rating ~ code + account_plan + priority for each code's
   CSAT drag, and the counterfactual CSAT if the top codes rated at baseline.
5. Target: at most 3 fixable root causes covering >=30% of Q3 volume, each with a likely owner team and a fix
   that can ship in Q4. Treat it as achievable; if the data says otherwise, report the real coverage.
6. Write one falsifiable prediction per recommendation. Save codebook, classifier and script so the identical
   run scores Q4 tickets.

Judges (not you):
- Before I see your labels, give me 100 random redacted tickets to label blind with the codebook. Report
  agreement (target >=80%) and revise the codebook if it falls short.
- Every number on a slide must come from a script output I can rerun; list them in an appendix.
- Finally, a fresh subagent with no shared context tries to break each headline claim from the raw CSV
  (duplicate tickets inflating a spike, a CSAT gap that is really a plan effect). Fix or drop what fails.
State the limits plainly: no resolution times, account IDs or revenue in this export.
```

Say "go" to run it, or pick another rung.
