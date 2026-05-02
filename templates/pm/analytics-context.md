# Analytics context

Living document for interpreting product analytics as part of **who we are now**.

This is not a full data warehouse export and not a replacement for live analytics. It captures the **reusable product meaning** of the data so PMs and agents do not rediscover which dashboards, segments, caveats, and metrics matter for every bet.

---

## Source

- **Tool:** [PostHog / Google Analytics / Amplitude / Mixpanel / warehouse]
- **Workspace / property / project:** [link]
- **Owner:** [person or team]
- **Agent access:** [direct query / human-mediated / restricted]
- **Default environment:** [production / staging / blended]

---

## Canonical views

| View | Link | What question it answers | Default segment | Default date range | Caveats |
| --- | --- | --- | --- | --- | --- |
| [Activation funnel] | [link] | [Where do users drop before first value?] | [segment] | [last 30 days] | [known issue] |

---

## Reusable product interpretations

Write short, durable interpretations that can inform many bets. Link to the live source and include the date range used.

| Date updated | Question | Interpretation | Evidence source | Confidence | Caveats | Related bets |
| --- | --- | --- | --- | --- | --- | --- |
| [date] | [e.g. Where do users drop in onboarding?] | [What we believe this means] | [view + date range] | [low / med / high] | [tracking gap, segment caveat] | [links] |

---

## Bet-specific analytics notes

When a bet needs a narrower readout, add a short note here or in the bet brief and link back.

| Bet | Question | Metric or view | Date range | Summary | Should this become reusable? |
| --- | --- | --- | --- | --- | --- |
| [bet link] | [question] | [view] | [range] | [1–3 bullets] | [yes/no] |

---

## Instrumentation gaps

| Gap | Why it matters | Owner | Status |
| --- | --- | --- | --- |
| [Missing event or property] | [Decision it blocks] | [Name] | [todo / in progress / done] |

---

## Rules for using this in bet briefs

- Use this file to find the **right** metric, dashboard, segment, and caveat.
- If a bet depends on a number, refresh the number from the live tool when access allows.
- Cite **tool + view + date range + segment** in the brief.
- If a one-off analysis reveals reusable knowledge, add a row under **Reusable product interpretations**.
