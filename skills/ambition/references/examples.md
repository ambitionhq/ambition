# Worked ladders

Six examples from different domains. Use them to calibrate what a good rung looks like: a bolder result that is startable, grounded and judged, with a number in it. Don't copy them. Every real ladder should come from the user's actual situation and the access they actually have.

These examples show every rung in full so you can calibrate. In a real reply, only the recommended rung gets full detail, and the other two get two lines each. See the output format in SKILL.md.

## Contents
1. Engineering: "Fix this crash"
2. Performance: "Make the site faster"
3. Product research: "Summarize these interviews"
4. Career: "Write my cover letter"
5. Learning: "Help me learn Spanish"
6. Creative: "Make a birthday video for my dad"

---

## 1. Engineering: "Fix this crash"

**Rung 0 · As asked:** Fix the crash when users upload a profile photo over 5 MB.
**Best axes:** Altitude + Depth. It's one instance of a class, and crash fixes are only as good as their reproduction.

### Rung 1 · Stretch (Depth)
Reproduce the crash with a failing test before touching the code, fix the root cause rather than the symptom, and fuzz the upload path with 1,000 generated images (sizes, formats, corrupted headers).
Needs: repo, test runner, an image fuzzing script · Judged by: the failing test goes green, and the fuzzer runs clean for an hour

### Rung 2 · Bold (Altitude)
Find every crash in the last 90 days with the same root cause (unbounded memory on media input) across all upload paths, fix them as one class, and add a lint rule or wrapper so new code can't reintroduce the bug.
Needs: crash reporting API access, symbolicated stack traces · Judged by: crash-free sessions on media screens, before vs after

### Rung 3 · Audacious (Altitude)
Keep the app crash-free without being asked. Watch new crash reports, map each to its commit, reproduce it on every target OS, open a PR with a regression test, and page a human only when it can't verify the fix. Run it in shadow mode (draft PRs only) for two weeks.
Needs: crash reporting API, version→commit mapping, macOS/Windows/Linux VMs, PR permission · Judged by: 99.9% crash-free sessions; share of PRs merged without changes

**Recommended: Rung 2.** Rung 3 needs VMs and access that don't exist yet. Rung 2 sets up most of them while delivering real value.
**Unlocks:** repo (have) · crash reporting API token (set up) · version→commit mapping (set up)

**What it would look like** (sketch):
```text
PR: Fix 7 crashes with one root cause (full-res decode before resize)
Evidence: 7/7 reproduced on device logs → 0/7 after fix · fuzzer clean for 60 min
Guard: lint rule `no-unbounded-decode` on all user-media paths
```

---

## 2. Performance: "Make the site faster"

**Rung 0 · As asked:** Our marketing site takes about 6 s to load. Make it faster.
**Best axes:** Depth. This is a measurement problem, and the 6 s figure probably came from someone's laptop.

### Rung 1 · Stretch (Depth)
Profile before changing anything: Lighthouse and WebPageTest traces on a throttled mid-range phone, plus a bundle analysis. Fix the three biggest costs and show the before/after waterfall.
Needs: site URL, repo, Lighthouse/WebPageTest CLI · Judged by: p75 LCP from repeated lab runs

### Rung 2 · Bold (Depth)
Target 200 ms to first meaningful paint on a 4G phone. Treat it as achievable. Consider static pre-rendering, edge caching, critical CSS inlining, and replacing the 400 KB framework on pages that don't need it. Log every approach tried.
Needs: hosting/CDN config access, build pipeline · Judged by: WebPageTest from 3 regions, median of 9 runs

### Rung 3 · Audacious (Depth + Altitude)
Make it impossible for the site to get slow again. Add a performance budget enforced in CI that fails any PR adding over 10 KB of JS or 50 ms of LCP, plus real-user monitoring with p75/p95 alerts.
Needs: CI config access, a RUM tool · Judged by: CI blocks a deliberately bloated test PR; RUM p75 stays under budget for 30 days

**Recommended: Rung 2, then Rung 3's budget.** The target forces structural fixes, and the budget keeps them.
**Unlocks:** repo (have) · CDN config (set up) · CI write access (set up)

**What it would look like** (sketch):
```text
WebPageTest · Moto G4 · 4G · median of 9
LCP 6.1 s → 0.38 s · JS 412 KB → 38 KB · requests 87 → 14
Not yet at 200 ms: hero font blocks first paint (next approach: subset + preload)
```

---

## 3. Product research: "Summarize these interviews"

**Rung 0 · As asked:** Summarize 20 customer interview transcripts into key themes.
**Best axes:** Depth + Range. Theme lists are the shallow default, and research has much sharper instruments.

### Rung 1 · Stretch (Depth)
Code all 20 transcripts with a jobs-to-be-done frame (struggling moment, desired outcome, current workaround), quote evidence for every claim, and count how many interviews support each theme.
Needs: transcripts · Judged by: every theme traces to at least 3 quoted interviews; a second independent coding pass agrees on 80%+ of the codes

### Rung 2 · Bold (Depth)
Challenge the roadmap. List the three beliefs the current roadmap rests on and test each against the transcripts *and* the product event logs. Report which beliefs survive.
Needs: transcripts, event logs/analytics export, the roadmap doc · Judged by: each verdict cites both what was said and what was done

### Rung 3 · Audacious (Range)
Run the analysis the way an intelligence agency handles conflicting sources. Rate each interviewee's reliability against their own usage data, weight claims by it, and give the top three opportunities as bets with confidence levels and a cheap test for each.
Needs: transcripts, per-user usage data · Judged by: each cheap test runs within two weeks and either confirms or kills its bet

**Recommended: Rung 2.** It turns research from a summary into a decision.
**Unlocks:** transcripts (have) · analytics export (set up)

**What it would look like** (sketch):
```text
Belief 2 of 3 does NOT survive: "Teams want more integrations"
Said: 14/20 interviews ask for integrations
Done: 2 of our 9 existing integrations carry 94% of usage; 4 have zero weekly users
Real ask, in their words: "I just need the Slack one to stop breaking" (P7, P12, P15)
```

---

## 4. Career: "Write my cover letter"

**Rung 0 · As asked:** Write a cover letter for a product designer role at a fintech startup.
**Best axes:** Range + Altitude. The letter is a means (getting a conversation), and recruiters, marketers and portfolio reviewers all know things here that a letter-writer doesn't.

### Rung 1 · Stretch (Depth)
Start from raw material, not a template: the job post, the company's last six months of product changes, and the team's public work. Write a letter whose first two lines would survive a 7-second skim.
Needs: job post URL, the company's site/changelog · Judged by: a cold reader can name the specific reason you fit after 7 seconds

### Rung 2 · Bold (Altitude)
The goal is the interview, not the letter. Find the hiring manager's stated priorities (talks, posts, job post language) and build a one-page redesign of a real friction point in their product, with the letter as its cover note.
Needs: the product (free tier), a design tool · Judged by: reply rate, compared with the plain letters you've sent before

### Rung 3 · Audacious (Range)
Run it like a direct-response campaign: a 3-variant test across five similar companies, tracking open and reply rates, then double down on the winner. Bring a recruiter's screening rubric in as the red team before sending.
Needs: a target list, a tracking sheet · Judged by: reply rates per variant

**Recommended: Rung 2.** One concrete piece of work beats any amount of polished prose.

**What it would look like** (sketch):
```text
Subject: I redesigned your transfer confirmation screen (1 page attached)

Your app reviews mention "did my money go through?" 200+ times since June.
The attached version answers that in the first second, without adding a screen.
I'd love 20 minutes to walk you through the reasoning.
```

---

## 5. Learning: "Help me learn Spanish"

**Rung 0 · As asked:** Make me a Spanish study plan.
**Best axes:** Altitude + Range. "Learn Spanish" is too vague to aim at, and coaching and memory research have much better methods than a plan.

### Rung 1 · Stretch (Altitude)
Pin down the real goal: hold a 20-minute conversation with my partner's grandmother at Christmas (8 weeks away). Build the plan backward from the topics she actually talks about.
Needs: a list of the topics and phrases that matter · Judged by: a 20-minute mock conversation at week 4 and week 8

### Rung 2 · Bold (Range)
Combine methods from three fields: spaced repetition (memory research) for the 800 highest-frequency words in her topics, deliberate practice with daily feedback (sports coaching), and minimal-pair drills for the sounds I get wrong (speech therapy).
Needs: an SRS app, recordings of my speech · Judged by: weekly recorded conversation scored against the CEFR A2/B1 speaking rubric

### Rung 3 · Audacious (Range + Depth)
Build a personal tutor loop. Every day, a 10-minute voice conversation about her topics, an analysis of my errors, and the next day's drills generated from those errors. Track error rate by category over time.
Needs: voice-capable assistant, an error log · Judged by: error rate per category trends down week over week; the real conversation at Christmas

**Recommended: Rung 2, with Rung 1's goal.** A specific person and date, plus methods that actually work.

**What it would look like** (sketch):
```text
Week 3 · Day 4 · 15 min
Cards due: 42 (her garden, her sister, the village festival)
Drill: /r/ vs /rr/ minimal pairs: pero / perro, caro / carro
Friday check: 10-min recorded chat → scored on the A2 rubric (last week: 2.5/5)
```

---

## 6. Creative: "Make a birthday video for my dad"

**Rung 0 · As asked:** Make a 3-minute birthday video from old family photos for my dad's 70th.
**Best axes:** Range + Depth. **Not Altitude.** The video *is* the point, and climbing to "the outcome" would wash out what makes it personal.

### Rung 1 · Stretch (Depth)
Edit like a documentary editor. Arrange the photos into a three-act story (who he was, who he became, who he made), pace the cuts to the music's tempo, and add slow Ken Burns moves on the faces.
Needs: scanned photos, one song, an editor (DaVinci Resolve is free) · Judged by: a sibling watches it cold and tells you where they felt something

### Rung 2 · Bold (Range)
Bring in an archivist and a sound designer. Restore the damaged photos (colorize, repair scratches, upscale), and record 30-second voice memos from 8 family members to lay under the photos they're about.
Needs: photo restoration tools, family members' phones · Judged by: a side-by-side of before/after restorations; family members recognize their own clips

### Rung 3 · Audacious (Range)
Add what a documentary crew would. Rebuild his childhood street in 3D from old photos and maps (Blender) for a 10-second opening fly-through, and grade every clip to one consistent film look.
Needs: Blender, reference photos/maps of the street, 2–3 weekends · Judged by: he recognizes the street before the caption appears

**Recommended: Rung 2.** The voices of the people he loves will matter more to him than any effect, and it's doable in a week.

**What it would look like** (sketch):
```text
0:00  Black. His sister's voice: "He was the one who climbed the water tower."
0:06  Restored 1961 photo fades up: the water tower, a boy halfway up
0:40  Act 2, who he became: the shop, the wedding, the first car (his own voice from a 1990s tape)
2:20  Act 3, who he made: eight grandkids, one line each, ending on the youngest
2:55  Hold on the water tower, today. Title: "Still climbing. 70."
```
