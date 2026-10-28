# Depth: do it the way the best in the field would

Depth is for when you just want the thing done *really* well. It means working the way a field-leading professional would: their raw material, their instruments, their standard of proof. Then you keep pushing until even that professional might learn something from the result.

Depth goes **down a layer**, from the digested report to the raw data, from symptom to mechanism, from opinion to measurement. It doesn't go sideways into more pages, more features or more words.

## Contents
- The depth probe
- Instruments, not vocabulary
- Unreasonable targets
- Challenge what everyone knows
- Produce new knowledge
- Outside judges
- Prompt templates

## The depth probe

Run this before writing any depth rung. It works as a prompt the user can reuse, too:

> Before doing this, go deeper, not bigger. Answer five things first:
> 1. **The pro's move**: what would a top practitioner in this field do here that I haven't asked for?
> 2. **The raw material**: what is the most primary source available, the thing before anyone summarized, charted or screenshotted it?
> 3. **The instruments**: which specific tools, methods and techniques would they use?
> 4. **The bar**: what result would they call excellent, and what would 10× that look like?
> 5. **The judge**: what, other than you or me, would show the result is right?
>
> Then rewrite my request so it asks for exactly that, and wait for me to say go.

## Instruments, not vocabulary

A model asked to "act like an expert" often switches its *vocabulary* but not its *methods*. It sounds like a statistician and then hands you a markdown table. The fix is to name the instruments. The user doesn't need to know them. You do.

| Field | Shallow default | What the best actually use |
|---|---|---|
| Data analysis | Pivot table, markdown summary | SQL / DuckDB on the raw export, regression, survival analysis for churn, cohort analysis, causal inference (diff-in-diff, matching), confidence intervals |
| Web performance | "Optimize images, minify JS" | Lighthouse + WebPageTest traces, real-user monitoring (p75/p95), flame graphs, bundle analysis, a performance budget enforced in CI |
| Debugging | Read the stack trace, guess | Reproduce reliably first, bisect (`git bisect`), add instrumentation, sanitizers (ASan/TSan), fuzzing, property-based tests |
| Security | Checklist review | Threat model (STRIDE), dependency audit, fuzzing, static analysis, writing an actual exploit for the finding |
| Writing | "Make it more engaging" | Reverse outline, line edit, cut 30%, read-aloud test, a cold reader who explains it back |
| Research / literature | Summarize top search hits | Primary sources, citation chasing both directions, effect sizes rather than headlines, replicating a key result from the paper's own data |
| Finance | Spreadsheet with growth assumptions | Driver-based model, sensitivity and scenario analysis, unit economics by cohort, forensic read of the footnotes |
| Product / UX | "Best practices" list | Session recordings, funnel analysis on event logs, usability tests with five real users, jobs-to-be-done interviews |
| ML | One model, one accuracy number | Strong baselines, held-out test set, ablations, error analysis by slice, calibration |
| Design / visual | Stock layout, generic assets | Real 3D (Blender), proper type scale, color grading, motion design, rendering at final resolution and checking it |

The rule: if the method didn't change, the depth didn't change. When you notice yourself reaching for a markdown table, ask whether a database, a model or a simulation would answer the question better.

## Unreasonable targets

Pick a goal that looks unreasonable, then tell the agent it is reasonable.

- They need the page to load in 5 s? Ask for 200 ms.
- They want to cut churn a bit? Ask for the signal that predicts churn 60 days out.
- They need tests for this module? Ask for 100% branch coverage plus a fuzzer that runs for an hour without a crash.

Why it works: a specific hard target rules out the comfortable approaches and forces structural ones. "A bit faster" invites minifying. "200 ms" invites rethinking the architecture.

When the model says the target is impossible, don't take that as the answer. Ask for three more approaches, each from a different angle, and try the most promising one. Keep a log of what was tried. The honest outcome might be "we reached 600 ms, and here's what blocks the rest." That's a great result, and the target is what got you there.

## Challenge what everyone knows

A lot of what organizations "know" is a rough approximation that hardened into fact. Depth means testing it against the raw data.

1. List the beliefs the task rests on, especially the ones nobody questions.
2. For each one, ask whether you could **reproduce it from the raw data**.
3. Argue against it: what would you expect to see if it were false? Look for exactly that.

> Everyone here says our best customers come from referrals. Using the raw signup and billing tables, check whether that holds once you control for plan and company size. If it doesn't, show me which channel really produces customers who stay and pay.

## Produce new knowledge

Once you're deep in the raw data anyway, look for something nobody knows yet, and *prove it*:

- **Find blind spots**: "What's the earliest signal of X that we don't track yet?"
- **Simulate**: "Before trusting a model to predict next year, make it reproduce last year from the raw logs."
- **Validate out of sample**: fit on one period and test on another the model never saw. A finding that only holds on the data it was found in is a story, not knowledge.

> Load two years of raw order logs. Using only the first year, find a leading indicator of demand spikes we don't track today. Then show how many days of warning it would have given on the second year, which you haven't looked at.

## Outside judges

The model judging its own work is the weakest evidence there is. For every depth rung, name an outside judge. The best ones are tools the agent can run itself and get feedback from right away:

| Work | Outside judge |
|---|---|
| Code | Tests, CI, type checker, sanitizers, reproducing the bug before and after |
| Performance | Profiler, benchmark, Lighthouse/WebPageTest, real-user metrics |
| Analysis / prediction | Held-out data, backtest, a pre-registered hypothesis |
| Writing / persuasion | A cold reader who explains it back, an A/B test, the actual decision-maker |
| Design | Five-user usability test, rendering at final size and resolution |
| Research claims | Primary source check, replication from raw data |
| Anything | An independent second run with no shared context, asked to find flaws |

## Prompt templates

**Go to the raw material:**
> Don't work from the summary/dashboard/screenshot. Get the raw <logs/export/source> and work from that. Tell me where the summary was misleading.

**Name the instruments:**
> Do this with the tools a top <field> professional would use. Name them first and say why. Don't present results in a markdown table unless a table is truly the best way to show them.

**Unreasonable target:**
> The target is <hard number>. It's achievable; keep going until you get there or can show exactly what blocks it. Log every approach you try.

**Adversarial check:**
> We believe <belief>. Try to reproduce that from the raw data. Then try hard to prove it wrong.

**New knowledge:**
> Once you've got the data loaded, find one thing about <domain> we don't already know, and show it holds on data you didn't use to find it.
