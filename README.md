<p align="center">
  <img src="assets/banner.svg" alt="ambition: your prompts are too small" width="100%">
</p>

<p align="center">
  <b>A skill that turns any task into the most ambitious version you can actually pull off, and then does it.</b>
</p>

<p align="center">
  <a href="https://agentskills.io"><img src="https://img.shields.io/badge/Agent%20Skills-compatible-FF8A4C" alt="Agent Skills compatible"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-3DD6C6" alt="MIT license"></a>
  <a href="prompt/ambition-prompt.md"><img src="https://img.shields.io/badge/also%20works%20in-ChatGPT%20%C2%B7%20Gemini-A78BFA" alt="Also works in ChatGPT and Gemini"></a>
</p>

<p align="center">
  <a href="#install">Install</a> ·
  <a href="#before--after">Before / after</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#tested-in-public">Tested</a> ·
  <a href="README.zh-CN.md">中文</a>
</p>

<p align="center">
  <img src="assets/demo.svg" alt="Demo: /ambition turns 'fix this crash' into a three-rung ladder" width="100%">
</p>

Most of us use AI for **speed**: the task we'd have done anyway, just faster. Meanwhile, other people are using the same models to keep whole apps crash-free, replace quarterly rituals, and find things in their data that nobody knew.

What separates the two groups isn't the model. It's the ask.

`ambition` fixes the ask. Give it any task and it hands back a **ladder**: three bolder versions of that task, each with what it needs and a check that doesn't involve the model grading itself. It sketches what the result would look like. You pick a rung, and it writes the prompt or does the work.

## Install

**Any coding agent:** Claude Code, Codex, Cursor, Gemini CLI, GitHub Copilot, and [many more](https://skills.sh).

```bash
npx skills add ambitionhq/ambition
```

<details>
<summary><b>Other ways to install</b></summary>

**Claude Code plugin**

```bash
/plugin marketplace add ambitionhq/ambition
/plugin install ambition@ambition
```

**Manual:** copy `skills/ambition` into your agent's skills folder (for Claude Code, `~/.claude/skills/`).

**Claude.ai / Claude Desktop:** download `ambition.skill` from [Releases](../../releases) and upload it under Skills in Settings.

**ChatGPT, Gemini, or any chatbot:** paste [`prompt/ambition-prompt.md`](prompt/ambition-prompt.md) into Custom Instructions, a GPT, a Gem, or a Project.

</details>

Then try it:

```text
/ambition <any task you were about to ask for>
```

## Before / after

Same model, same question:

> *My manager asked me to put together 5–6 slides summarizing our Q3 customer support tickets. I have a Zendesk CSV export (~4,200 tickets). How could I be way more ambitious with this?*

**Without `ambition`:** a thoughtful list of eight ideas for a better deck.

**With `ambition`:** a three-rung ladder. Rung 1 sorts tickets by root cause from the raw text. Rung 2 (recommended) turns the review into three decisions. Rung 3 is a weekly root-cause watch. Then a recommendation, the unlocks, the trust risks, and a sketch of what the first slide would look like:

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

It ends with a paste-ready prompt: reconcile with Zendesk's own numbers first, redact personal data, classify every ticket from its text, have you label 100 tickets blind to check the classifier, and have a fresh agent try to break every headline.

The sketch uses made-up numbers. Read the **full, unedited outputs** of both runs in [`showcase/`](showcase/).

## How it works

There are four ways to be more ambitious with a model. The first is the default. The other three are where the leverage is.

| Axis | The move | Example |
|---|---|---|
| **Speed** | Same task, less time | Write this function faster |
| **Altitude** ↑ | Solve the outcome behind the task | *Fix this crash* → *keep the app crash-free* |
| **Depth** ↓ | Do it the way the best in the field would: raw data, real instruments, hard targets | *Summarize tickets* → *classify 4,200 raw tickets by root cause and test what everyone believes* |
| **Range** ↔ | Borrow methods from fields nobody invited | *Make a birthday video* → *restore the photos like an archivist, layer in family voice memos like a sound designer* |

Every ladder goes through the same steps:

1. **Rung 0.** Restate what you literally asked for, and take stock of what's on hand.
2. **Pick the axes that fit.** It knows when *not* to climb. Altitude flattens creative work, for example.
3. **Build three rungs:** Stretch, Bold, Audacious. Each one must be a bigger *result*, startable in minutes, grounded in real inputs, and judged from outside the model, with a number in it.
4. **List the unlocks**, including whose buy-in you need, and the **trust risks** that would sink it.
5. **Name the outside judge:** tests, held-out data, a backtest, a profiler, a real user.
6. **Recommend one rung, sketch the result, and hand back a paste-ready prompt.**

## What makes it different from "think bigger" prompts

- **Every rung is startable.** No "leverage AI to transform your workflow." If an agent can't begin in five minutes, the rung gets rewritten.
- **The model never grades itself.** Every recommendation comes with an outside check.
- **Methods, not personas.** It won't ask the model to *"write like a short seller"*. It asks it to *do what a short seller does*: hunt for the reason the story is false.
- **You see it before you commit.** Each ladder includes a sketch of the actual result: the alert, the slide, the pitch.
- **Honest about the cheap path.** If an off-the-shelf tool already does rung 1, it says so.
- **The ladder is a menu.** It never quietly widens what you asked for. You pick the rung.

## Commands

| Command | What it does |
|---|---|
| `/ambition <task>` | Ladder: three rungs, a recommendation, a sketch, and an upgraded prompt. Doesn't start the work. |
| `/ambition go` | Runs the chosen rung against its outside judge. Shadow mode first, and it asks before anything risky. |
| `/ambition audit` | Looks back over your conversation or project and finds the three places you aimed lowest. |
| `/ambition depth <task>` | One axis only (`altitude`, `depth`, or `range`). |

It also triggers on plain language, in any language: *"be more ambitious"*, *"think bigger"*, *"10x this"*, *"what am I missing?"*, *"格局打开"*.

## Examples

Worked ladders across six domains are in [`examples.md`](skills/ambition/references/examples.md):

| Domain | Rung 0 | Rung 3 |
|---|---|---|
| Engineering | Fix this crash | Keep the app crash-free, in shadow mode |
| Performance | Make the site faster | A CI performance budget that makes slow impossible |
| Product research | Summarize 20 interviews | Weight claims by each interviewee's real usage, then bet |
| Career | Write my cover letter | Run it like a direct-response campaign |
| Learning | Make me a Spanish study plan | A daily tutor loop built from your own errors |
| Creative | A birthday video for Dad | A 3D fly-through of his childhood street |

**Share yours.** Real ladders with real results go in the [gallery](gallery/). See [CONTRIBUTING.md](CONTRIBUTING.md).

## Tested in public

We ran three test tasks (a Chinese-language data pipeline, a support-ticket review and a short story) with and without the skill, on the same model. An independent grader agent scored every output.

| Task | Checks passed (with / without) | Which answer the grader would rather receive |
|---|---|---|
| Support-ticket review | 12/12 · 8/12 | **With ambition.** A decision-ready plan and a runnable analysis brief |
| Daily Shopify report (Chinese) | 13/13 · 10/13 | **With ambition**, narrowly. The baseline reads more warmly |
| Sci-fi short story | 13/13 · 9/13 | **Without.** The plain model's concept was more original |

The checks partly measure structure (is there a ladder, a judge, a paste-ready prompt?), so the pass rates flatter the skill. The last column is the honest one. There was one run per configuration, so treat these as a sanity check, not a benchmark. We kept iterating where the skill lost. Round 1's story ladder was all process, and that led to the rule that every rung must be a bigger *result*. All outputs are in [`showcase/`](showcase/).

Plain frontier models are already good at brainstorming. What `ambition` adds is consistent structure: measurable targets, outside judges, a concrete sketch, honest unlocks and a prompt you can run. The test cases are in [`evals/`](evals/). Run them yourself:

```bash
claude plugin eval .
```

## FAQ

**Isn't this just a prompt?**
Yes, and so is most of what makes people good with models. This one is structured, tested, and opinionated about the failure modes: role play, self-grading, scope creep, and "bigger" passed off as "deeper".

**Will it make every task huge?**
No. Ladder mode doesn't start any work. Rung 1 is often the right answer, and it'll tell you when it is.

**Does it work outside Claude?**
Yes. `SKILL.md` is an open standard supported by most coding agents, and [`prompt/ambition-prompt.md`](prompt/ambition-prompt.md) works in any chatbot.

**Why "ambition"?**
People, and the models that take their cue from people, aim at what they believe is possible. Specific hard goals, existence proofs and permission to fail all measurably raise what gets attempted. See [why-it-works.md](skills/ambition/references/why-it-works.md).

## Credits

The four-axis framework (Speed, Altitude, Depth, Range) comes from Felix Rieseberg's essay [*How to be more ambitious: A tutorial for humans with models*](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models) (October 2026). Read it; it's short and excellent. The "nouns into verbs" technique comes from Tom Kelley and Jonathan Littman's *The Art of Innovation*.

This is an independent community project. It is not affiliated with or endorsed by Anthropic or the essay's author.

## License

[MIT](LICENSE)
