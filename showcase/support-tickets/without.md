Keep it to 5-6 slides. Being ambitious here means the slides say more, not that there are more of them. The default deck reports what happened: volume, priority mix, CSAT, open vs. closed. A more ambitious deck explains why it happened, what it cost, and what to do in Q4. Your manager walks out with decisions to make, not just numbers to nod at.

Here's how I'd raise the bar, roughly in order of payoff.

## 1. Read all 4,200 descriptions, not just the tags

Zendesk tags are usually messy. Agents apply them, so they overlap and are often missing. The real signal is in `subject` and `description`. I can sort every ticket into a clean set of categories (for example, product area plus issue type: bug, how-to confusion, billing, account access, feature request, integration) and give each one a likely root cause.

That changes "we had 4,200 tickets" into something like "a third of our tickets come from six causes, and four of them can be fixed." Every other idea below builds on this.

To keep it credible, hand-check a random sample of about 100 classifications and put the agreement rate in the appendix. That one line answers "can we trust this?" before anyone asks.

## 2. Put a price on each problem

Ranking issues by volume is fine. Ranking them by cost is what gets people to act. For each top driver, show:

- Ticket count, share of total, and the July to September trend
- Average CSAT for that driver, so you can see which issues leave customers angriest
- Which plans it affects. A problem concentrated in your top plan matters more than its raw count suggests.
- A rough cost: tickets times a handling cost per ticket. Get that number from your support lead or finance, and state it as an assumption.

That "top fixable drivers" table will probably be the most useful slide in the deck.

## 3. Explain CSAT instead of just reporting it

One CSAT number doesn't tell anyone what to do. Ask instead what predicts a bad rating: topic, plan, priority, repeat issues. Pull 3-4 real, anonymized quotes from low-rated tickets about the top driver. In a review meeting, one customer's own words do more than any chart.

Put a caveat on the slide: only some customers leave a rating, and they tend to be the ones with strong feelings. Show the response rate next to the score.

## 4. Find what's emerging, not just what's big

The biggest categories are usually things everyone already knows about. The more interesting finding is what's growing: issues that were small in July and much bigger by September, or weekly spikes that line up with a release or an incident. If you can get a list of Q3 release dates, I can plot them against weekly volume for each category. A finding like "one August release caused about 300 tickets about X" is the kind people remember.

## 5. Size the deflection opportunity

Some tickets are questions that a help article, an in-app hint, or a clearer error message would have answered. Flag them as "could have been self-served" and size the total: roughly N tickets a quarter, plus the top 10 questions behind them. That's a concrete Q4 project with a target you can measure.

## 6. Connect tickets to revenue (the big swing)

Your CSV has `account_plan`, but no account ID and no revenue. If you can get the account or org ID from Zendesk and join it to ARR and renewal/churn data from your CRM or billing system, you can answer what executives actually care about: do accounts with certain ticket patterns churn more? Even a simple comparison works, such as "accounts with 5+ Q3 tickets, or any ticket about X, renewed at Y% vs. Z% overall." People will quote that slide for months.

This idea has the biggest impact and takes the most effort, and it depends on access you may not get before Thursday. One Slack message will tell you whether it's possible.

## 7. End with asks, not a summary

Make the last slide three concrete recommendations. Give each one an owner, an expected drop in tickets, and a way to measure it in Q4. For illustration:

- "Fix the SSO error message (Eng, about 250 tickets a quarter)"
- "Write 10 help articles (Support, about 400 tickets a quarter)"
- "Add an escalation path for Enterprise billing issues (Support Ops)"

This presents support as the team that finds and sizes the company's problems, not a cost center reading out numbers.

## 8. Make it repeatable

If the analysis is a script rather than a one-off spreadsheet, the Q4 review takes an hour instead of a week. You can also track the same drivers quarter over quarter, which is how you'd show the Q3 recommendations worked. Going further, you could send product teams a monthly "top drivers" digest, or hand out a small interactive explorer for anyone who wants to dig in.

---

## A possible 6-slide outline

1. **The headline:** one sentence and three numbers (volume vs. Q2, CSAT, share of tickets from fixable causes).
2. **What drove volume:** top drivers ranked by ticket count, with trend arrows.
3. **What hurt customers most:** CSAT by driver and plan, with one or two customer quotes.
4. **What's new or growing:** emerging issues and spikes tied to releases.
5. **The opportunity:** how many tickets, and how much cost, deflection and fixes could remove.
6. **Asks for Q4:** three recommendations, with owners and targets.

**Appendix:** methodology and classification accuracy, the full category list, definitions, and the standard stats (priority mix, status, weekly volume) for anyone who wants them.

## Check these before starting

- **Q2 data.** Without a comparison, the numbers have nothing to anchor them. A Q2 export (and Q3 of last year, if seasonality matters) is the cheapest improvement you can make.
- **Missing fields.** The export has no solved or first-reply timestamps, no agent, and no account ID. Resolution time and first-response time are standard review metrics. If your manager expects them, re-export with those fields now, not the night before.
- **Data hygiene.** Confirm the date range and timezone, remove spam, merged, and duplicate tickets, and remember that tickets still open at export time will skew the status numbers.
- **Customer data.** Descriptions probably contain names, emails, and maybe sensitive details. Check your company's policy on running ticket text through an AI tool, and anonymize any quotes that go on slides.
- **Your manager's expectations.** Going from "summary" to "root causes and recommendations" is only a good surprise if it isn't a surprise. Send a two-line heads-up: "I'm planning to go beyond counts into drivers and Q4 recommendations. Anything you want me to dig into or avoid?" The reply will also tell you who the audience is and what they care about.

## What's realistic by Thursday

If you share the CSV, ideas 1-5 and 7 take a day or two of back-and-forth. I'd clean the data, propose categories for you to adjust, classify every ticket, run the breakdowns, and draft the storyline before we touch any slides. Idea 6 depends on getting the account and revenue data. Idea 8 is easy if we build the analysis as a script from the start.

Three answers would shape the plan:

1. Who's in the room: support leadership, product/engineering, or executives?
2. Can you get a Q2 export, and an export that includes account ID and solved timestamps?
3. Did anything happen in Q3 (a launch, an incident, a pricing change) that the review will want explained?
