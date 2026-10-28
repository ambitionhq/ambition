# Altitude: solve the outcome, not the task

When someone hands a model a task, the task is their best guess at how to get some outcome. Altitude means stepping back from the guess and working on the outcome itself. The payoff is large. You stop feeding the model task after task, and you end up with workflows that keep working without a human in the loop.

## Contents
- The "and then what?" chain
- From instance to class to loop
- Designing the durable loop
- Where altitude stops working
- Shadow, don't replace
- Prompt templates

## The "and then what?" chain

Five Whys runs backward to a root cause. This chain runs forward to the real goal. Starting from the literal task, ask *"when this is done, what do you want to happen next?"* and keep going until the answer is something a person cares about for its own sake.

```
Update the QBR slides with Q3 numbers
  → and then?  Leadership reviews them in the meeting
  → and then?  They decide where to put money and people next quarter
  → and then?  Problems get caught early and resources move to what works
```

Each hop is a candidate rung. The last hop is usually rung 3. Stop climbing when the next hop needs authority or access that nobody in the room has.

A good sign that altitude will pay off is that **someone is going to hold a meeting about this**. Meetings exist to turn information into decisions. If the deliverable feeds a meeting, a higher rung can usually do some of that meeting's work ahead of time.

## From instance to class to loop

Most recurring work climbs in the same three steps:

| Level | Example (engineering) | Example (operations) |
|---|---|---|
| **Instance** | Fix this crash | Answer this refund email |
| **Class** | Fix every crash with this root cause; add a guard so the category can't come back | Find the five reasons people ask for refunds and fix the top one at the source |
| **Loop** | Keep the app crash-free: watch crash reports, reproduce, fix, verify, open a PR, all without being asked | Keep refund requests below 1% of orders: watch, diagnose, propose changes, measure |

The jump from class to loop is where the human leaves the loop. It's also where most of the setup work is.

## Designing the durable loop

A loop runs without new instructions only if the agent can **see**, **act** and **check** on its own. Go through each one:

1. **Trigger**: what starts a cycle? A new crash report, a schedule, a threshold being crossed.
2. **Inputs**: can the agent fetch the raw signal itself? Think crash reports, logs, tickets, metrics.
3. **Context**: can it connect the signal to the thing it needs to change? For example, which app version maps to which commit, or which customer maps to which plan.
4. **Act**: can it make the change in a safe place? A branch, a draft, a staging environment.
5. **Verify**: can it confirm the fix worked *independently*? Reproduce the bug before and after, run tests, check on every platform that matters.
6. **Escalate**: when does it stop and ask a human? Spending money, touching production, anything it couldn't verify.

Each "no" in that list is an **unlock**, a one-time setup task. Setting up those unlocks is often the most valuable piece of the whole project. Changing the workflow so the agent can verify things on its own beats any amount of prompt cleverness.

A typical unlock list for "keep the app crash-free":
- programmatic access to the crash reporting service
- a mapping from release version to git commit
- machines or VMs for every target OS, so the agent can reproduce and verify fixes itself
- permission to open PRs (not merge them) and a rule for when to page a human

## Where altitude stops working

- **Creative work.** If the point is the artifact (a story, a song, a painting, a video), climbing to "the outcome" tends to wash out the very thing that makes it good. Use depth and range instead.
- **Missing access.** The ceiling is whatever the agent can reach, change and verify. "Go make money" fails for most businesses today, not because the model isn't clever enough, but because it can't see, act on or check most of what that would take. Above the ceiling, the next thing to do is the setup that raises it.
- **Missing authority.** Some outcomes belong to people who haven't agreed to hand them over. A rung that redesigns another team's process is a proposal, not a task. Frame it that way.

That said, the ceiling rises with each model generation. Check the current one rather than assuming last year's still holds.

## Shadow, don't replace

High rungs often replace an existing process. Never rip the old one out first. Run the new system **beside** the old one for a while (a cycle, a month, a quarter) and compare:

- Backtest: "Using our own history, show that the new approach would have caught X sooner."
- Shadow run: "Run it in parallel for one cycle; don't act on its output yet."
- Graduate: let the new system take over once the judge says it is better.

This lowers the risk of the audacious rung enough that people actually say yes to it.

## Prompt templates

**Climb one level:**
> The task I asked for is a means to an end. The end is: <outcome>. Don't just do the task. Tell me what would most move that outcome, using everything in <data/sources>, and do that instead if it's within reach. If it isn't, do the task and tell me what access would let you do the bigger version.

**Instance to class:**
> Fix this <bug/problem>, then find every other case with the same root cause in <codebase/data>, fix those too, and add a guard (test, lint rule, validation) so this category can't come back. Show me the before/after evidence for each.

**Design the loop:**
> I want <outcome> to stay true without my asking. Design the loop: trigger, inputs, context, action, verification, escalation. For each step, tell me whether you can do it today with the access you have. Then set up everything you can, and list the unlocks you need from me.

**Replace the ritual:**
> <Ritual> exists so that <real purpose>. Design a better way to achieve that purpose. Show from our own history that it would have worked better, then propose running it beside the current process for one cycle.
