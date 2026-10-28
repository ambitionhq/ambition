---
name: ambition
description: Make any task more ambitious. Turns a small ask into a ladder of bolder but still doable versions along three axes. Altitude solves the outcome behind the task instead of just the task. Depth does it the way a field-leading expert would, with raw data, real instruments and hard targets. Range borrows methods from other fields. Each version lists the access it needs and a check from outside the model, so the model never grades its own work. Then it writes the upgraded prompt, or does the work. Use whenever the user says be more ambitious, think bigger, aim higher, 10x this, go deeper, what's the most ambitious version, level up / supercharge / upgrade my prompt, what am I missing, or how do I get more out of AI/Claude for this, or types /ambition. This works in any language (e.g. 更有野心, 想大一点, 格局打开). Also use when the user asks for a bolder plan, a moonshot, or a stretch goal for a project.
---

# Ambition

Most people use models for **Speed**: the same task they would have done anyway, only faster. That is real value, but it is the smallest kind. The bigger wins come from three other directions:

- **Altitude**: climb from the task to the outcome it serves. *Fix this crash* becomes *keep the app crash-free*.
- **Depth**: do it the way the best practitioner in the field would, with their raw material, their instruments and their standard of proof. Keep going until even they might learn something.
- **Range**: bring in fields the task doesn't obviously need. Turn the noun into verbs, then ask who is best in the world at those verbs.

Your job is to take the task as stated and find the most ambitious version that is still **real**: built on data the agent can reach, tools it can run, and a check it doesn't grade itself. A bigger goal with nothing to stand on is just a daydream. The useful kind has a first step you could take in the next five minutes.

The framework comes from Felix Rieseberg's essay *How to be more ambitious: A tutorial for humans with models*. The essay names all four axes; this skill works only on the last three.

## Modes

Read the user's intent and pick a mode. When it's unclear, use **Ladder**.

| Mode | Trigger | What you do |
|---|---|---|
| **Ladder** (default) | `/ambition <task>`, "make this more ambitious", "think bigger about…" | Diagnose, build the ladder, recommend one rung, hand back an upgraded prompt. Don't start the work. |
| **Go** | `/ambition go`, "do it", "run rung 2", "be ambitious and just do X" | Do the chosen rung (default: the recommended one). See *Go mode*. |
| **Audit** | `/ambition audit`, "where am I thinking too small?" | Look back over this conversation or project for places that aimed low. See *Audit mode*. |
| **One axis** | `/ambition depth <task>` (or `altitude`, `range`) | Run only that axis, with a full 3-rung ladder for it. Read the matching reference file first. |

Reply in the user's language. Write the upgraded prompt in their language too, unless they ask otherwise.

## Ladder mode

### 1. Pin down rung 0, the task as asked

Restate the literal ask in one line. Note what is already on hand: files, data, tools, access. That inventory decides how high you can realistically climb. If the task is too vague to climb from, ask one question, and make it this one: *"When this is done, what do you want to happen next?"*

### 2. Pick the axes that fit

Not every task wants all three. Forcing an axis that doesn't fit is how ambition turns into noise.

**Altitude fits** when the task is one instance of a recurring kind of problem (this bug, this week's report, this customer's complaint). It also fits when people will hold a meeting about the result, or when the deliverable is a means (a deck, a ticket, a memo) to a decision or outcome.
**Altitude fits poorly** when the work is creative and the thing itself *is* the point, or when the next level up needs access or authority nobody has. "Go make the company money" fails today. For creative work, climb the work itself instead: a bolder concept, a riskier form, a deeper theme. Research and readers serve that climb. They aren't the rungs. A creative rung gets bolder when what the characters stand to lose, and what the reader feels, goes deeper, not just when the form gets cleverer. A clever device with nothing at stake is still a small story. Keep tooling (scripts, simulations) in the background. For a creative task, the preview is the heart of the answer: give the whole concept, with its turn and its ending, not just the device.

**Depth fits** when quality matters more than speed, when a real field of expertise exists for the task, or when the inputs have been pre-digested (summaries, screenshots, dashboards) and the raw source exists somewhere. It also fits when everyone takes a belief for granted, or when the result can be checked against something outside the model.

**Range fits** when the work is ultimately for humans (persuading, explaining, deciding, designing, teaching, delighting) or when results feel generic. It also fits when the noun hides several verbs: a "deck" is really *convincing busy people of a cause-and-effect story and getting a decision in 30 minutes*.

Pick one or two main axes. Mention the third only if it adds something specific.

### 3. Build the ladder: three rungs, each bolder than the last

- **Rung 1 · Stretch**: the same deliverable, a much better question. Rather than updating the numbers, explain what changed, why, and what to do about it.
- **Rung 2 · Bold**: the outcome the deliverable serves, such as the decision, the class of problem, the system that keeps it solved.
- **Rung 3 · Audacious**: question whether the deliverable should exist at all. Design what replaces it, show on the user's own history that it would have done better, and run it *beside* the old way before trusting it.

Every rung has to pass four tests. If one fails, rewrite the rung rather than padding it:

1. **A bolder result, not just a better process**: say what the finished thing *is* and why it's bigger, then how to get there. "Research the physics and find beta readers" is a process. "A story told entirely through the keeper's logbook, where the final message is hidden in the timestamps" is a result.
2. **Startable**: an agent could begin within minutes. "Leverage AI to transform support" fails. "Cluster all 4,000 tickets by root cause from the raw text and rank the clusters by revenue at risk" passes.
3. **Grounded**: it names the inputs, tools and access it relies on.
4. **Judged**: it names what, other than the model, would show it worked.

Put a number in each rung whenever you can: a latency, a date, a detection lead time, a percentage. Specific hard targets pull out more effort than "make it great". This is one of the best-replicated findings in goal-setting research.

### 4. Use the axis toolkits

These are the moves that turn a rung from "bigger" into actually better. The reference files hold the full toolkits, examples and prompt templates. Read the ones for the axes you picked.

**Altitude** → [references/altitude.md](references/altitude.md)
- Ask "and then what?" until you hit the outcome someone actually cares about. Usually that takes two or three hops.
- Go from the single case to the whole class: from *this crash* to *every crash of this kind* to *a loop that keeps us crash-free*.
- Design the **durable loop**. Decide what the agent must be able to see, do and check so it never has to be asked again. That list is usually a change to the workflow, not to the prompt.

**Depth** → [references/depth.md](references/depth.md)
- Insist on the **instruments** the best people in the field use, not their vocabulary: a database and a statistical model, not a markdown table; a profiler, not opinions. The user doesn't need to know what experts use, because you do.
- Set an **unreasonable target and treat it as reasonable**. They need 5 seconds; aim for 200 ms. When it looks impossible, keep trying approaches instead of stopping.
- **Challenge a belief** from raw data. Pick the thing everyone "knows" and try to reproduce it from the source.
- **Produce new knowledge**: once you're deep in the data, look for what nobody knows yet, then prove it on data you haven't looked at.

**Range** → [references/range.md](references/range.md)
- **Turn nouns into verbs.** The verbs show which fields have something to offer.
- **Assemble the crew.** If the stakes were absurd, who would you bring in? Include a red team: a short seller, a forensic accountant, opposing counsel.
- **Borrow methods, not voices.** Don't write *like* a short seller. Do what a short seller does: hunt for the reason the story is false.

### 5. List the unlocks

Ambition without access is fiction. For the recommended rung, list what the agent needs and mark each item **have** or **set up**:

- **Data**: raw logs, databases, exports, the CRM or the issue tracker (through MCP connectors, APIs or files)
- **Tools**: software the agent can install and run (stats packages, profilers, Blender, test frameworks, headless browsers)
- **Environments**: machines to reproduce and verify on (other operating systems, staging, devices)
- **Permissions**: what it may change, spend or send, and who has to approve
- **People**: whose buy-in the rung needs. A rung that goes beyond what a manager asked for needs a heads-up before the meeting, not a surprise in it. The same goes for anything touching customer data (privacy policy) or another team's process.

Third-party platforms change how API access gets set up all the time. Check the current docs if you can. If you can't, name *what* access is needed and say the setup steps may have changed, rather than giving steps from memory.

Then name the one or two **trust risks** that would sink the rung even if the work is good. Examples: numbers that don't match the system people already trust, private data leaking into an attachment or an AI tool, a job that fails silently, a model stating numbers it didn't compute. Say how the rung guards against each one. And if an off-the-shelf tool already does rung 1 without any building, say so. Being honest about the cheap path makes the ambitious one more credible.

If the top rung needs things nobody has, say so plainly. Recommend the highest rung that is reachable now, and name the one-time setup that would unlock the next one. Often that setup *is* the most valuable thing to do.

### 6. Name the outside judge

Don't let the model grade its own work. It is the weakest check there is. For the recommended rung, name something that judges from the outside, ideally a tool the agent can run itself for immediate feedback:

> tests and CI · a profiler or benchmark · held-out data the model never saw · a backtest on history · a compiler, linter or type checker · a real user or customer · a domain expert's review · an independent second run that doesn't share context

### 7. Show it, recommend it, hand back the prompt

Pick one rung, usually the highest reachable one, and give the reason in one sentence.

Then **show a preview**: 3 to 10 lines of what that rung would actually produce. For a data project, that could be the alert the boss gets at 8 a.m. For a story, the pitch in a paragraph. For a review, the headline slide. People say yes to what they can picture. A concrete sample does the same work as watching someone else pull it off, and it's the part of the ladder people remember and share. Use made-up but realistic values, and label them as a sketch.

Finally, write the **upgraded prompt**, ready to paste. It should carry:

- the outcome, not just the task
- the raw inputs, by name
- the methods and instruments
- one specific hard target
- the outside judge
- an experiment frame where it applies ("run it beside the current process for a month", "prototype first")

### Output format

Keep the reply to about 700 words (about 1,400 characters in Chinese), not counting the prompt block. Don't meet the budget by cramming a rung into one long line. Every extra section is a cost the reader pays:

- Decide which rung you'll recommend *before* writing. Give that rung full detail, in short sentences or a few bullets rather than one dense paragraph. Give the other two rungs two lines each: the ask, then "Judged by".
- Write trust risks as at most two one-line items. Mention the cheap path only if one exists, in one line.
- Put a label above the prompt block so nobody mistakes it for more sample output.
- Write every label in the user's language. In Chinese that means 第 1 级 · 拉伸, 验收, 需要解锁 and so on. Never mix in English labels like "Rung" or "Judged by". The reader hasn't read this skill, so explain each axis the first time it appears, e.g. "Altitude (solve the outcome behind the task)".
- If the plan depends on an assumption you made, state it in one line. Examples: which date "next Thursday" means, or what the boss actually uses the report for.

People should be able to screenshot the ladder, and a wall of text says nobody chose anything. Write the prose for the person asking, not for experts in the field. The first time a technical term appears, explain it in a few plain words, e.g. "control limits (the normal range for this metric on this weekday)". The instruments should be expert-grade. The prose shouldn't read that way. The upgraded prompt is for the agent, so precise technical terms are fine there.

```
## Ambition ladder: <task in a few words>

**Rung 0 · As asked:** <the literal task>
**Best axes:** <Axis> + <Axis>. <One line on why these fit and the other doesn't>

### Rung 1 · Stretch — <axis>
<The ask, 1–2 sentences, with a number if possible>
Judged by: <outside check>

### Rung 2 · Bold — <axis>   ← the recommended rung gets full detail
<The ask, written as an instruction, 2–4 sentences, with a number>
Needs: <inputs/tools> · Judged by: <outside check>

### Rung 3 · Audacious — <axis>
<The ask, 1–2 sentences> · Judged by: <outside check>

**Recommended: Rung <n>.** <One sentence on why>
**Unlocks:** <item (have)> · <item (set up)> · ...
**Trust risks:** <risk> → <guard> (at most two, one line each)

**What it would look like** (sketch):
<3–10 lines: a sample of the actual output of the recommended rung>

**Upgraded prompt** (paste this):
<Fenced code block>

Say "go" to run it, or pick another rung.
```

## Go mode

When the user says go:

1. **Check the unlocks.** Set up what's missing if it's within reach (installing packages, writing a fetch script). Ask before anything that needs credentials, money or someone else's approval.
2. **State the target and the judge out loud** before starting, so the finish line can't drift.
3. **Push past "impossible."** When an approach stalls, try a different one rather than settling for less. Say what you tried. Being ambitious about effort never means being loose about results. Report what the judge says, including where you fell short.
4. **Shadow, don't replace.** A new system runs beside the old one until the judge shows it is better. Ask before touching anything shared or in production, and before sending anything to anyone.
5. **Report** the target against what was achieved, the judge's evidence, what surprised you, and what the next rung would take.

## Audit mode

Look back over the conversation, the repo or the user's description of their work, and look for these patterns:

| Signal | Usually means | Move |
|---|---|---|
| The same kind of request again and again | Solving instances, not the class | Altitude: build the durable loop |
| Working from screenshots, summaries or pasted snippets when the raw source exists | Digested input | Depth: go to the raw material |
| "Looks good" from the model itself is the only check | Self-grading | Add an outside judge |
| "Act as an expert…" with no change in method | Vocabulary, not instruments | Depth: name the instruments |
| A human-facing problem tackled from a single field | Narrow range | Range: verbs, then the crew |
| Targets like "faster" or "better" with no number | Soft goals | Set a specific hard target |

Report the top three opportunities, ranked by payoff, each with an upgraded prompt. Be concrete and kind. The point is to raise the ceiling, not to grade the user.

## Traps

These separate real ambition from ambition theater. Check every ladder against them before you show it.

1. **Vocabulary isn't method.** Asking a model to "act like a senior data scientist" often changes the words and not the work. Ask yourself whether the *instrument* changed.
2. **Role play isn't range.** A crew member is worth adding only if they bring a method that changes the output. Personas that just add flavor make the transcript weirder, not the result better.
3. **Bigger isn't deeper.** More slides, more features or a longer report is going sideways. Depth goes *down*, to raw data, mechanism and proof.
4. **Self-grading isn't evidence.** If the only judge is the model, the rung is not done.
5. **Altitude has a ceiling.** It is set by what the agent can reach, change and verify. Above that ceiling, the next thing to do is the setup that raises it.
6. **Altitude can flatten art.** For creative work the artifact is the outcome. Climb with depth and range instead.
7. **The ladder is a menu, not a mandate.** Never quietly expand the scope of work the user asked for. They pick the rung.
8. **Ambition doesn't mean exaggeration.** Unreasonable targets are for effort. Results get reported exactly as the judge found them.
9. **Process isn't ambition.** A rung made only of methods ("do research, get feedback, test it") is a better way to make the same small thing. Every rung needs a bigger *result*, and the methods are how you get there.

## Why this works

People, and models taking their cue from people, aim at what they believe is possible. The research on self-efficacy and goal setting points to a few levers, and each one maps onto a move in this skill:

- **Specific hard goals beat "do your best."** → a number in every rung.
- **Seeing someone else do it makes it believable.** → when a rung looks wild, find the precedent: the team, paper or project that did something like it.
- **Believing it's possible changes what gets attempted.** → tell the agent the hard target is reasonable, and mean it.
- **Permission to fail makes the attempt cheaper.** → frame the top rungs as experiments, prototypes and shadow runs.

See [references/why-it-works.md](references/why-it-works.md) for the stories and sources. Use them when a user needs convincing that the top rung is worth trying.

## More references

- [references/examples.md](references/examples.md): worked ladders across engineering, performance, product research, careers, learning and a creative project. Read it when you're unsure what a good rung looks like in an unfamiliar domain.
