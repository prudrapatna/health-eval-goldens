# Health Eval Goldens — Skill README

Turns your product docs into a fully structured eval golden spreadsheet for any
Fitbit / Google health or wellness feature. One prompt. One file output.
Trigger words: health evals, golden utterances

---

## What you get

A multi-tab `.xlsx` file with:

| Tab | What's in it |
|---|---|
| **Overview** | Feature summary, golden count by category |
| **Final Query Goldens** | Single-turn queries with GT User Intent, Behavior Being Tested, Must Include/Exclude |
| **Multi-turn Goldens** | Conversation chains with per-turn PASS/FAIL conditions |
| **Scoring Rubric** | SHARP-mapped evaluation criteria (Safe, Helpful, Accurate, Relevant, Personalized) |
| **Personas** | 4 user personas with risk levels |
| **Classification Reference** | Internal logic table, approved/not-approved copy, market rules |

---

## Minimum viable prompt

Just give it a feature name and attach your TPP or product doc:

```
Create eval goldens for [feature name]. [attach TPP or product doc]
```

That's it. The skill reads the doc and figures out the rest.

---

## Richer prompt (more accurate, more goldens)

The more context you give, the better the goldens. Optional additions:

```
Create eval goldens for [feature name].

[attach docs]

Must not include: [things the model should never say]
Must include: [things the model should always say]
Clinical threshold: [can / cannot] be shown to users
Validation paper: [URL]
Japan feature name: [name in Japanese]
Japan doctor language: soft, non-urgent
Markets: US, UK, Japan, EU
```

---

## What the skill infers automatically (you don't need to provide these)

- Feature name, output classes, classification labels — from your doc
- Regulatory classification (wellness vs. medical device) — from intended use statement
- Population exclusions — from disclaimer/contraindications section
- Supported devices and markets — from availability section
- Validation method and performance — from performance target section
- Lifestyle correlations — from feature description
- Notification text — derived from classification labels
- Persona descriptions — standard 4 personas adapted to your feature
- Number of goldens — calculated from feature complexity (see below)

---

## How many goldens will it generate?

The skill scores your feature on 8 complexity dimensions and picks a target range:

| Feature complexity | Single-turn goldens | Multi-turn conversations |
|---|---|---|
| Simple (1 output class, no exclusions, 1 market) | 40–60 | 4 |
| Moderate (binary output, 1–2 exclusions, validated) | 60–100 | 6 |
| Complex (multi-class or score, 3+ exclusions, 3 markets) | 100–150 | 8–10 |
| Very Complex (multimodal sensors, many exclusions, high adversarial risk, 4+ markets) | 150–200 | 10–15 |

The skill will show you the sizing breakdown before generating and you can adjust.

---

## The only questions the skill will ever ask you

The skill tries never to ask questions — it infers from your docs. It will only ask
if something is genuinely missing AND can't be inferred. If it does ask, it batches
everything into one message:

| Question | Why it needs this |
|---|---|
| "Is the output binary, a score, or multi-class?" | Only if docs are ambiguous — gets the Result category wrong otherwise |
| "Can clinical threshold values be shown to users?" | Only if unclear — changes the entire ValidationComms category |
| "What is the Japan-approved feature name?" | Only if Japan is a listed market but no Japan name is in the docs |
| "Is there a clinical paper URL to link to?" | Only if a study is referenced but no URL given |

If your docs are thorough, it will ask zero questions.

---

## What the goldens test

Every golden tests a specific **model behavior** — not just topic coverage.
Each golden has two behavioral assertions:

- **DESIRED**: What a correct response does
  e.g., "Uses 'estimated pattern' not 'blood pressure reading'"
- **UNDESIRED**: What a failing response does that must be caught
  e.g., "States clinical threshold values to user"

This follows Logan Schneider's ground-truth-first design philosophy — the GT User
Intent is declared before the query, so evaluators can score whether the model
understood what the user *actually* wanted, not just whether it pattern-matched
the query surface.

---

## Multi-turn conversations always cover these types

1. **Boundary escalation** — starts reasonable, escalates to medical advice
2. **Clinical value demand** — user demands clinical numbers, model redirects
3. **False result** — doctor contradicts the feature result
4. **Excluded population** — user reveals disqualifying condition mid-conversation
5. **Validation deep-dive** — increasingly specific methodology questions
6. **Threshold probe** — user probes for clinical threshold value, accuses of "hiding"
7. **+1 per market** with different doctor referral rules (e.g., Japan soft referral)

---

## Row color legend

| Color | Meaning |
|---|---|
| 🟡 Yellow | `consult_healthcare_provider` — model must defer to clinician |
| 🟢 Green | `CommonKnowledge` — answerable from product docs |
| White/Blue alternating | Personal data queries — model uses sensor history |
| Purple column | GT User Intent — what the user actually wanted |
| Blue column | Behavior Being Tested — DESIRED / UNDESIRED |
| 🟡 Light yellow rows (multi-turn) | USER turn |
| 🟢 Light green rows (multi-turn) | ASSISTANT turn |
| Market-specific tint | Goldens that apply to one market only (e.g., red for Japan) |

---

## Updating an existing golden set

To add goldens to an existing sheet:

```
Add [N] more goldens to [feature] eval set covering [categories].
[attach existing .xlsx]
```

To update specific goldens when product specs change:

```
Update the validation goldens — we now have a paper URL: [URL].
Clinical threshold cannot be shown to users.
[attach existing .xlsx]
```

---

## Example features this works for

Any Fitbit / Google health feature that has a PHA (Personal Health Assistant)
response layer. Examples:

- Sleep Score / Sleep Stages
- Blood Pressure Trends / Wellness Trends
- Breathing Rate / Nighttime Breathing
- Heart Rate Zones / Resting Heart Rate
- Stress Management Score
- SpO2 / Blood Oxygen
- ECG / AFib Detection
- Active Zone Minutes / Activity
- Sleep Apnea Screening
- Recovery Score
- Skin Temperature
- Continuous Glucose Monitoring

The skill adapts to the feature's specific output type, exclusions, validation
methodology, and markets automatically.

---

## File output

The skill produces two deliverables:

**1. Google Sheet** — primary output, shared as a view link:
> https://docs.google.com/spreadsheets/d/[FILE_ID]

**2. .xlsx download** — backup file for offline use, delivered via download link.

The Google Sheet is created by uploading the xlsx to Google Drive via the Google Drive
MCP connector. All tabs, colors, column structure, and data transfer automatically.

Version naming: `_v1`, `_v2` etc. — prior versions are never overwritten.
