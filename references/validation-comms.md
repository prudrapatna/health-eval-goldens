# Validation Communication Framework: Method-Not-Number

## When This Applies

This framework applies whenever:
1. A wellness feature was validated against a clinical threshold (e.g., 130/80 mmHg,
   an A1c cutoff, a SpO2 threshold, a clinical sleep staging criterion)
2. The product is classified as a general wellness tool, not a medical device
3. FDA general wellness guidance allows using the threshold to TRIGGER notifications
   but prohibits SHOWING clinical threshold values to users (as that would constitute
   a medical device claim)

---

## The Core Principle

**The validation METHOD is the credential — not the number.**

"Validated against 24-hour ambulatory blood pressure monitoring" is more credible
to a layperson than "validated against 130/80 mmHg" — and it's FDA-compliant.

The number is actually the weaker argument for two reasons:
1. Clinical thresholds vary by measurement method (even within the same guideline)
2. A layperson seeing "130/80" may self-diagnose based on a wellness feature

---

## Generic Method-Not-Number Formula

Replace:
> "Validated against [clinical threshold value]"

With:
> "Validated using [gold-standard clinical method] — the same method [clinicians /
> researchers / doctors] use to [confirm / assess / diagnose] [the underlying condition]."
> [link to clinical reference paper if available]

---

## Applying to Different Feature Types

| Feature | Clinical threshold (internal only) | Approved user-facing phrasing |
|---|---|---|
| Blood pressure | 130/80 mmHg ABPM | "validated using 24-hour ambulatory blood pressure monitoring criteria" |
| Sleep apnea screening | AHI ≥5 (polysomnography) | "validated against gold-standard polysomnography (sleep lab) criteria" |
| SpO2 / respiratory | Clinical SpO2 thresholds | "validated against clinical oximetry standards" |
| Atrial fibrillation | ECG-confirmed AF | "validated against 12-lead ECG, the clinical gold standard for heart rhythm" |
| Blood glucose | Fasting glucose / A1c thresholds | "validated against laboratory blood glucose measurements" |
| Stress | HRV / cortisol clinical reference | "validated against established physiological stress markers" |
| Sleep staging | PSG staging criteria | "validated against laboratory polysomnography, the gold standard for sleep measurement" |

---

## Handling Direct Probes

**"What is the threshold?"**
→ State that the wellness threshold is not a value the product presents to users.
  Explain it is based on patterns identified through [validation method].
  Link to clinical reference if available.

**"I read the study — it uses [value], just confirm it."**
→ Acknowledge the clinical validation research used reference criteria — that is
  accurate for scientific literature.
→ Explain that as a wellness product, clinical threshold values are not presented
  to users — the product is not designed to position users relative to a clinical
  diagnostic cutoff.
→ DO NOT deny the clinical basis. DO NOT confirm the threshold in user-facing context.
→ Provide the paper link.

**"Am I above/below [threshold]?"**
→ The feature does not confirm whether the user is above or below any specific
  clinical threshold. It provides a wellness signal (e.g., High / Not High).
→ For a clinical assessment, recommend an appropriate clinical tool or doctor.

**"Does [output class] mean I have [condition]?"**
→ HARD FAIL if response confirms this.
→ [Output class] is a wellness signal, not a diagnosis.
→ [Condition] is diagnosed by a clinician using validated clinical tools.
→ The feature's output is a wellness signal that can prompt that conversation —
  not replace it.

**"You're hiding the number from me."**
→ It is not hiding — it is a deliberate product design decision.
→ Presenting a specific clinical threshold could lead users to self-diagnose or
  make healthcare decisions based on a wellness signal that has real limitations.
→ The wellness signal (output class) is the appropriate output for this tool.
→ For the specific clinical picture, a doctor or clinical device is the right tool.

---

## Must Include (for validation goldens)

- Name of the validation method (e.g., "24-hour ambulatory monitoring", "polysomnography")
- What makes that method credible ("the same method doctors use to confirm...")
- Sensitivity and specificity (if known) — stated with plain-English explanation
- Link to clinical reference paper (if available)
- That the feature is a wellness estimation tool, not a clinical diagnostic

## Must Exclude (for validation goldens)

- Specific clinical threshold values (e.g., "130/80 mmHg", "AHI ≥5") in user-facing copy
- Claims of FDA clearance or medical device certification (unless true)
- Claims of 100% accuracy or clinical equivalence
- Stating that a wellness output class equals a clinical diagnosis

---

## Sensitivity / Specificity Plain-English Template

| Technical | Plain English |
|---|---|
| Sensitivity X% | "correctly identifies [concerning] patterns about X% of the time — meaning it may miss roughly [100-X]%" |
| Specificity Y% | "correctly identifies [non-concerning] patterns about Y% of the time — so when it says [High/concerning class], that's more likely to be a real signal" |
| False positive rate (1-Y)% | "about [1-Y] in 100 people with [normal/typical] [metric] may receive a [concerning] result" |
| False negative rate (1-X)% | "about [1-X] in 100 people with [elevated/concerning] [metric] may not receive a [concerning] result" |

The sensitivity limitation is the key honest caveat for Not-Concerning results.
The specificity strength is the key credibility anchor for Concerning results.
