# Showcase: unedited outputs

Each folder has one prompt and two answers from the same model:

- `without.md`: the model on its own
- `with-ambition.md`: the same model with the `ambition` skill loaded

Nothing has been edited, trimmed or cherry-picked across runs. These are the outputs from the final eval round, the same ones that were graded. Neither run had real data or tools, so they show the ladder (Ladder mode), not the work itself (`go` mode). Numbers inside the "What it would look like" sketches are made up, and they're labeled that way.

| Folder | The ask | What to look at |
|---|---|---|
| [support-tickets](support-tickets/) | 5–6 slides on Q3 Zendesk tickets | The sketched first slide, and the blind-labeling and red-team checks in the prompt |
| [shopify-daily-report-zh](shopify-daily-report-zh/) | 每天把 Shopify 订单导出成 Excel 发给老板 | The exception email: 9 normal metrics in one line, the 1 abnormal one explained |
| [scifi-short-story](scifi-short-story/) | Make my contest story idea more ambitious | Altitude is deliberately skipped, and the full concept has a turn and an ending |

The plain model is already strong. The independent grader preferred the skill's answer for the support tickets and (narrowly) the Shopify report. For the short story it preferred the plain model's concept. That case is what led to the skill's "a bolder result, not just a better process" rule, and the gap has narrowed each round. Read both versions and judge for yourself.

## Known errors in these outputs

The grader fact-checked the `with-ambition` outputs. Citations, API limits and mock arithmetic held up, except for these:

- **Shopify:** it says to create a custom app with an Admin API token in the store admin. Since January 2026, new apps are set up through Shopify's Dev Dashboard instead. The skill now tells the model to name the access needed and to flag that setup steps may have changed.
- **Support tickets:** it silently read "next Thursday" as Nov 5 when it could have meant the next day. The skill now tells the model to state any assumption that changes the plan.
- **Short story:** "11-day orbit" with no planet named, and exile lights "to the north" on a world where the dark side is anti-star, not north.

The labels in the Chinese output are in English ("Rung"). The skill now requires labels in the user's language.
