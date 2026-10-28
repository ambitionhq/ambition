# Range: bring in the fields nobody invited

Range means looking at the work from the perspective of other fields, and more of them than would ever have been economical to staff. Every heist movie spends its first act assembling a crew of very different specialists, and that's the instinct here. With subagents and parallel threads, adding a crew member now costs minutes, not a hiring round.

Range is where the most surprising results tend to come from. It's also the hardest axis to use, because it takes imagination. Someone who has built video games might still never think to render their homepage in a 3D engine until they see someone else do it. This file exists to lower that bar.

## Contents
- Turn nouns into verbs
- Assemble the crew
- Methods, not voices
- Running a crew with subagents
- Verb → field catalogue
- Tools borrowed from other fields
- Prompt templates

## Turn nouns into verbs

This technique comes from Tom Kelley and Jonathan Littman's *The Art of Innovation*. A noun hides what the work actually does, and verbs show it.

| Noun | Verbs |
|---|---|
| A quarterly review deck | get busy people to believe a cause-and-effect story, and decide under uncertainty, in 30 minutes |
| A README | earn a stranger's trust in 10 seconds, get them to a working install in 2 minutes |
| A cover letter | survive a 7-second skim, make one specific person want a conversation |
| A birthday video | make people laugh and cry at the same moments, preserve memories for 30 years |
| An onboarding flow | teach without lecturing, get to the first win before attention runs out |

Each verb points to fields that are world-class at it. That gives you the crew.

## Assemble the crew

Raise the stakes until they're absurd: *"If this doesn't work, the world ends. Who does humanity send?"* That framing gives you permission to cast far wider than the task seems to need.

For a quarterly business review (the example the original essay uses), the crew might be:
- **Production**: an analyst (finds the story), a journalist (leads with what matters), an editor (cuts everything else)
- **Delivery**: a motion designer and an audio designer, if it will be presented
- **Red team**: a short seller (hunts for why the story is false), a forensic accountant (checks whether the numbers tie out)

Always include a **red team**. Adversarial fields such as short sellers, opposing counsel, pen testers, peer reviewers and investigative journalists are the cheapest way to find the hole before someone else does.

## Methods, not voices

The most common failure is **role play**: asking the model to *write like* someone. The transcript gets more colorful and the result doesn't improve. Use the crew to find **fields and techniques**, then ask for what those people *do*.

| Role play (doesn't help) | Method (helps) |
|---|---|
| "Write this like a short seller" | "Do what a short seller does before shorting: list every claim this story depends on and look for evidence each one is false" |
| "Review this as a lawyer" | "Do what opposing counsel would do in discovery: find the single document or sentence that undermines our position" |
| "Make it sound like a film editor cut it" | "Cut it the way an editor would: map the emotional beat of every section, then remove anything that doesn't change the beat" |
| "Act as a UX researcher" | "Run a five-user think-aloud test script against this flow and list every place a user hesitates" |
| "Pretend you're a game designer" | "Design the progression the way a game designer would: what's the first win, how fast does it arrive, and what's the reward loop after it?" |

Check every crew member with one question: **what does this field's method add to the output that wouldn't be there otherwise?** If you can't name it, drop the crew member.

## Running a crew with subagents

When the environment supports subagents or parallel threads:

1. **Brief each crew member with a method and a deliverable**, not a persona. ("Using forensic accounting methods, reconcile these three reports and list every number that doesn't tie out.")
2. **Run them in parallel** on the same raw material.
3. **Synthesize**: one pass merges the findings, resolves conflicts and decides.
4. **Red team last**: a fresh agent with no shared context attacks the synthesis.

When there are no subagents, do the same thing in sequence, with an explicit section per method.

## Verb → field catalogue

| Verb | Fields worth borrowing from |
|---|---|
| Persuade | trial lawyers, speechwriters, direct-response copywriters, fundraisers |
| Explain | science journalists, teachers, museum curators, technical illustrators |
| Decide under uncertainty | intelligence analysts, poker players, actuaries, emergency physicians |
| Hold attention | film editors, game designers, stand-up comedians, magicians |
| Find the truth | investigative journalists, auditors, epidemiologists, detectives |
| Make it feel like something | composers, sound designers, cinematographers, set designers |
| Build trust | doctors (bedside manner), negotiators, hospitality, pilots (checklists and calm) |
| Simplify | industrial designers, editors, cartographers, sign designers |
| Make it reliable | aviation safety, SRE, nuclear operations, surgical checklists |
| Grow something | gardeners, community organizers, epidemiologists (spread models) |
| Teach a skill | sports coaches, music teachers, speech therapists, language acquisition researchers |
| Remember | archivists, oral historians, photo restorers, librarians |

## Tools borrowed from other fields

Range applies to instruments too. Some tools that cross over well:

- **3D engines (Blender, game engines)**: product shots, interior mockups, explainer scenes, hero images that aren't stock
- **Simulation (agent-based, Monte Carlo)**: business planning, queueing, capacity, epidemics of anything
- **GIS and mapping**: any problem where *where* matters, such as sales territories, delivery, site selection
- **Audio tools (DAWs, sound design)**: presentations, videos, product feel
- **Statistical process control (from manufacturing)**: any metric you watch over time
- **Checklists (from aviation and surgery)**: any recurring high-stakes process
- **Spaced repetition (from memory research)**: onboarding, training, learning

## Prompt templates

**Verbs first:**
> Before doing this, rewrite "<noun>" as the three or four verbs it actually needs to accomplish. For each verb, name the field that's best in the world at it and the specific method they'd bring.

**Assemble the crew:**
> Imagine the stakes are absurdly high. Assemble a crew of 4–6 specialists from different fields, including at least one red-teamer. For each one, give the method they contribute and the concrete artifact it adds. No role play: I want their techniques, not their voices.

**Red team:**
> Do what <adversarial field> does: find the strongest reason this is wrong, using <raw material>. Then tell me what would have to be true for the original to survive.
