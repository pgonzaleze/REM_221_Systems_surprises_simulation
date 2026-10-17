# Hollow Bay: When good solutions create new problems

An interactive systems-thinking simulation created for the Systems Thinking course, REM 221 at SFU. 

You are the coastal management team of a fictional fishing community. Over 20 simulated years, you make four decisions, one every five years, to protect fish stocks, sustain community wellbeing and manage a limited public budget.

Your decisions have delayed effects, feedback loops and unintended consequences, and the system will surprise you.

**[▶ Play it online](https://pgonzaleze.github.io/REM_221_Systems_surprises_simulation/)**

---

## Contents

- [Why this exists](#why-this-exists)
- [Features](#features)
- [How to play](#how-to-play)
- [How the simulation works](#how-the-simulation-works)
- [Project structure](#project-structure)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [License](#license)

---

## Why this exists

Many real-world problems get worse when we treat only the most visible symptom. Hollow Bay lets learners experience that firsthand, then gives them the vocabulary to explain what happened.

By playing, learners practise recognising:

- **Feedback loops**, both reinforcing and balancing
- **Delays** between an action and its effect
- **Limiting factors** and shifting constraints
- **System boundaries**, such as effort displaced to neighbouring waters
- **Unintended consequences** of well-meant interventions
- **Systems archetypes**, such as Fixes That Fail and Shifting the Burden

## Features

- **Four decision rounds** (Years 0, 5, 10 and 15) with four options each, giving 256 possible paths and very different outcomes
- **Predict-then-reveal loop**: write what you expect to happen, then compare it with the consequences
- **Personalised debrief** built from your own decisions:
  - A chart of fish stock, habitat and wellbeing over the 20 years, with turning points
  - The *hidden variables* the dashboard never showed (effective pressure, compliance, trust, displaced effort)
  - Seven systems archetypes ranked by how strongly your choices triggered each one, with evidence from your run, the loop, a leverage point and a discussion question
- **Tailored adaptive management plan** that identifies the binding constraint, sorts your decisions into keep, rework and add, and gives review triggers with numbers from your final state
- **Save the report as PDF** through the browser's print dialog
- **Single file, zero dependencies**: no build step, no frameworks, no network requests, and no data leaves the browser
- **Accessibility basics**: keyboard focus styles, `aria-live` feedback regions, a responsive layout and `prefers-reduced-motion` support

You can also double-click `index.html`. Chrome, Edge, Firefox and Safari are supported.

## How to play

1. Click **Start the simulation**.
2. Read the scenario and choose one intervention.
3. **Write a prediction**: what do you expect to happen, and when?
4. Click **Commit to this decision** to see what happened over the next five years.
5. Repeat for four rounds, then work through the debrief.
6. Optionally write a reflection, generate the management plan, and **Save report as PDF**.

There is no perfect option. The score is a prompt for discussion, not a forecast.

## How the simulation works

Hollow Bay is a deliberately simplified teaching model, not a calibrated fishery model. Each decision applies immediate effects, then a five-year loop plays out year by year.

**Visible indicators** (the dashboard): public budget, fish stock, habitat health, community wellbeing. All are 0–100 indices.

**Hidden variables** (revealed in the debrief): fishing pressure, rule compliance, community trust, displaced effort, excess fleet capacity, alternative income and a tourism flag.

Key dynamics:

| Mechanism | What it models |
| --- | --- |
| **Effective fishing pressure** | Formal pressure plus pressure hidden in overcapacity and displaced effort, adjusted for how well rules are followed |
| **Overfishing** | Above roughly 55, fish stock declines, with larger losses as pressure rises |
| **Recovery needs two things** | Below roughly 45, stock rebuilds only if nursery habitat is healthy, so habitat work alone stalls when pressure stays high |
| **Collapse and slow recovery** | Below about 25, decline can feed on itself and rebuilding is much slower than the decline was |
| **Capacity lock-in** | Subsidised equipment outlasts the subsidy and weakens later restrictions until livelihood support retires it |
| **Legitimacy** | Enforcement backfires when trust is low, and reversing earlier rules costs extra trust |
| **Displaced effort** | Restrictions with no income alternative push effort into neighbouring waters or unreported fishing |
| **Income loss** | Lower effort cuts incomes until the stock rebuilds or alternatives exist |
| **Limits to growth** | Tourism expansion damages the habitat it depends on |
| **Social feedbacks** | Low wellbeing and low trust erode compliance and push pressure back up |

## Customising the game

Everything lives in `index.html`. Look for these parts of the `<script>` block:

- **`rounds`**: the scenario text, questions and choices (`id`, `name`, `desc`, `cost`) for each round.
- **`applyDecision(id)`**: the immediate effect of each choice, in a `switch` statement.
- **The `for (let yearStep...)` loop**: the five-year dynamics and thresholds.
- **`eventText`**: the explanatory messages shown after each round.
- **`diagnose()`**: the archetype rules and evidence text.
- **`buildPlan()`**: the logic behind the tailored management plan.
- **`initial`**: the starting values of the system.

To adapt the scenario, for example to a river, forest or urban setting, change the text in `rounds` and the explanatory strings, then adjust the numbers in `applyDecision` and the loop. If you add a new choice `id`, add a matching `case` in `applyDecision`.

## Project structure

```
REM_221_Systems_surprises_simulation/
├── index.html   # The whole game: HTML, CSS and JavaScript
├── README.md
└── LICENSE
```

## Limitations

- Indicators and outcomes are **illustrative**. They are not calibrated to any real fishery and must not be used to make real management decisions.
- The model is deterministic: the same choices always give the same result. This is intentional so teams can compare runs, but it means there is no random variation.
- Saving to PDF uses the browser's print dialogue. If the page is opened inside an embedded preview, printing may be blocked, so open the file in a normal browser tab.


## License

This project is licensed under the [GNU General Public License v3.0](https://github.com/pgonzaleze/REM_221_Systems_surprises_simulation/blob/main/LICENSE) (GPL-3.0). You are free to use, study, share and modify it, including for teaching. If you distribute a modified version, it must also be released under GPL-3.0 with its source code available.

---

*Hollow Bay is a fictional teaching simulation created for educational purposes.*
