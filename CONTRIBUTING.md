# Contributing

The most valuable contribution is a **real ladder that worked**: a task you actually ran through `ambition`, which rung you picked, and what the outside judge said.

## Add a ladder to the gallery

1. Copy [`gallery/TEMPLATE.md`](gallery/TEMPLATE.md) to `gallery/<domain>-<short-name>.md`, for example `gallery/data-churn-signal.md`.
2. Fill it in. Strip anything confidential, such as company names, customer data or internal URLs.
3. Open a PR titled `gallery: <one-line description>`.

What gets merged:
- **Real results over hypotheticals.** "We reached 640 ms, down from 6 s" beats "this could be faster."
- **An outside judge.** Say what proved it worked. A ladder whose only check is "Claude said it looked good" won't be merged.
- **Honest misses.** A rung that failed, and why, is just as useful as one that worked.

## Improve the skill

- Keep [`SKILL.md`](skills/ambition/SKILL.md) under ~300 lines. Detail belongs in `references/`.
- Explain *why* a rule exists instead of adding MUSTs. The model follows reasons better than orders.
- If you change behavior, add or update an eval case in `evals/` and run, from the repo root:

```bash
claude plugin eval .
```

## Translations

Translations of the README are welcome as `README.<lang>.md`. The skill itself replies in the user's language, so `SKILL.md` stays in English.
