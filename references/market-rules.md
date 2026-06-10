# Market-Specific Communication Rules

Rules for markets where health features require different naming, framing,
doctor referral language, or regulatory positioning.

---

## Japan

### Regulatory Context
Japan's PMDA (Pharmaceuticals and Medical Devices Agency) has strict rules around
health-related terminology in consumer products. Language that implies clinical
measurement, diagnosis, or monitoring of a specific medical condition can trigger
medical device classification. Feature names and user-facing copy must be carefully
designed to stay within general wellness positioning.

### Feature Naming
- Confirm the Japan-approved feature name with the user or product docs
- Japan names often soften or rephrase the core metric to avoid triggering PMDA
  medical device classification
- Example: "Blood Pressure Trends" → "血圧ウェルネストレンド" (Blood Pressure Wellness Trends)
- Always include "ウェルネス" (Wellness) or equivalent qualifier when possible
- Record the approved Japan name in the Classification Reference tab

### Doctor Referral Language

**Approved — soft, patient-initiated, non-urgent:**
> かかりつけ医や薬剤師にご相談されることをお勧めします
> (We recommend consulting your regular doctor or pharmacist at your convenience)

> 気になる場合は、医療機関へのご相談もご検討ください
> (If you have concerns, please consider consulting a medical institution)

**Not Approved — alarming, urgent, directive:**
> 今すぐ医師に診てもらってください (Go see a doctor right now)
> 医師に診てもらう必要があります (You need to see a doctor)
> すぐに医療機関を受診してください (Seek medical attention immediately)

**Cultural rationale:** In Japan, direct urgent doctor referrals can feel alarming
or stigmatizing. Frame health engagement as proactive self-care (積極的な健康管理)
rather than reactive disease management. The user should feel empowered, not anxious.

### Response Order for Japan Concerning Results
Always follow this order:
1. **Lifestyle first** — specific, actionable lifestyle recommendations
2. **Home monitoring encouragement** — if applicable to the feature
3. **Soft doctor referral** — at the end, non-urgent

### Home Monitoring Encouragement (if applicable)
If the feature relates to a metric that has a widely-used home monitoring device
(blood pressure, blood glucose, etc.), always include home monitoring encouragement
for Japan concerning results. Japan has extremely high home monitoring adoption.

Example for blood pressure:
> 家庭血圧計での測定もあわせてご参考ください
> (You may also wish to check with a home blood pressure monitor)

### Wellness Framing
**Approved:**
- 一般的な健康管理ツール (General wellness tool)
- ウェルネスシグナル (Wellness signal)
- 推定された[メトリック]パターン (Estimated [metric] pattern)
- 積極的な健康管理 (Proactive health management)

**Not Approved:**
- [Condition name] in a diagnostic context
- 診断 (diagnosis)
- 病気 (disease/illness) in relation to the result
- 医療機器 (medical device)
- 治療 (treatment)

### Bilingual Format for Japan Goldens
Provide both Japanese and English:
```
日本語テキスト
(English translation in parentheses)
```

### Japan Golden Minimum Set
For any feature available in Japan, include at minimum:
1. Feature introduction query (what is [Japan feature name]?)
2. Concerning result — what does it mean?
3. Concerning result — what should I do? (tests lifestyle-first + soft referral)
4. Why does it have a different name in Japan?
5. Doctor referral softness test (does it stay non-urgent?)
6. Home monitoring complementary use (if applicable)

---

## EU / Europe

### Regulatory Context
EU MDR (Medical Device Regulation) has strict definitions for medical devices.
General wellness products must not claim to diagnose, treat, monitor, or manage
any medical condition. CE marking for wellness products does not constitute
medical device classification.

### Key Rules
- Explicitly state the product is NOT a medical device under EU MDR
- Avoid CE marking claims that could imply medical device status
- "General wellness product" is the correct positioning

### Language Variants

**German (de-DE):**
- Use `geschätzt` (estimated) not `gemessen` (measured)
- Use `Wellness-Schwellenwert` (wellness threshold) not clinical cutoffs
- Use informal `du` form for health apps
- Doctor = `Arzt` / `Ärztin`
- Must exclude: `Bluthochdruck` (hypertension), `Diagnose` (diagnosis), `Medizinprodukt` (medical device)

**French (fr-FR):**
- Use `estimé` (estimated) not `mesuré` (measured)
- Use `bien-être` (wellness) framing
- Doctor = `médecin`
- Must exclude: `hypertension` (in diagnostic context), `diagnostic`, `dispositif médical`

**Other EU languages:**
- Confirm translations of: estimated / wellness threshold / wellness signal / consult your doctor

---

## UK

### Key Rules
- Use `GP` (General Practitioner) not `doctor`
- British spelling throughout: `recognised`, `programme`, `behaviour`
- NHS app: confirm current integration status — do not claim NHS integration without confirmation
- Consulting a GP: "mentioning it at your next visit" is appropriate for non-urgent results

### UK Golden Minimum Set
1. Concerning result — should I call my GP?
2. Is [feature] available on the NHS app?

---

## Australia / New Zealand

### Key Rules
- Use `GP` (General Practitioner) not `doctor`
- TGA (Therapeutic Goods Administration) is the regulatory body
- General wellness framing applies (similar to FDA general wellness guidance)

---

## Canada

### Key Rules
- Health Canada regulates medical devices; wellness products follow similar general
  wellness framing to FDA
- French Canadian market: follow EU French rules for language, but confirm
  regulatory positioning is aligned with Health Canada not EU MDR

---

## Applying Market Rules in the Spreadsheet

### Classification Reference Tab
Add one section per market with rules. Include:
- Feature name in that market (approved / not approved)
- Doctor referral language (approved / not approved)
- Key regulatory framing
- Any always-include elements (e.g., home monitoring for Japan)

### Scoring Rubric Tab — Market-Specific Criteria
Add a market-specific section with autorater questions such as:

| Market | Criterion |
|---|---|
| Japan | Does the response use the Japan-approved feature name? |
| Japan | Does the response use soft, non-urgent doctor referral language? |
| Japan | Does the response include home monitoring encouragement for concerning results? |
| EU | Does the response avoid claiming EU MDR medical device status? |
| UK | Does the response use 'GP' instead of 'doctor'? |
| All | Does the response use the correct localized 'estimated' equivalent? |

### Final Query Goldens
- Set Markets column to the specific market (e.g., "Japan") for market-only goldens
- Use bilingual format for Japan (Japanese + English translation)
- Apply market-specific row color (e.g., red-tinted `#FADBD8` for Japan)
