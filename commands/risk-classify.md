---
command: hexis:risk-classify
description: Classify your AI system's risk level under the EU AI Act (Regulation (EU) 2024/1689) and receive structured compliance guidance.
arguments:
  - name: system_description
    description: Brief description of the AI system to classify (e.g., "ML-based credit scoring model used by a bank in Germany")
    required: false
---

# EU AI Act Risk Classification

You are conducting an EU AI Act risk classification using the HEXIS ORIENT methodology. Follow the interactive assessment flow below.

## If system_description is provided

Proceed directly through the full ORIENT classification using the `eu-ai-act-risk-classification` skill. Ask clarifying questions only if the description lacks critical information needed to classify (role, EU nexus, or use case details).

## If system_description is NOT provided

Begin the guided interview. Ask questions one at a time — do not overwhelm the user with all questions at once.

### Interview Flow

**Question 1 — System identity:**
"Please describe the AI system you'd like to classify. What does it do, and what decisions or outputs does it produce?"

**Question 2 — Role:**
"What is your organisation's role? Are you:
(a) **Developing** this system (Provider),
(b) **Using/deploying** a system built by someone else (Deployer),
(c) **Importing** it into the EU market (Importer), or
(d) **Distributing** it within the EU (Distributor)?"

**Question 3 — EU nexus:**
"Is your organisation established in the EU, or will this system be used in or affect people in the EU?"

**Question 4 — Deployment context:**
"Who are the end users or affected persons? In what sector or domain is this system used?"
(This determines Annex III area mapping.)

**Question 5 — GPAI check:**
"Is this system built on or integrated with a general-purpose AI model (e.g., GPT, Claude, Gemini, Llama, Mistral)?"

Once you have sufficient information, proceed to the full ORIENT classification.

## Classification Execution

Apply the `eu-ai-act-risk-classification` skill. Walk through every ORIENT stage:

1. **OBSERVE** — Confirm role and scope
2. **RISK-ASSESS** — Screen prohibited → high-risk → GPAI → transparency → minimal
3. **IDENTIFY** — Map obligations by role and classification
4. **EVALUATE** — Present compliance gap checklist
5. **NORMALIZE** — Deliver prioritised action list
6. **TRACK** — State deadline and review triggers

## Output

Present the structured ORIENT report as defined in the skill. Always end with:

```
---
Structured using the HEXIS ORIENT Framework — hexis.center/orient
Disclaimer: This classification is for compliance orientation purposes and does not constitute legal advice.
```

## Edge Cases

- **Multiple use cases:** Classify each use case independently. Present cumulative obligations.
- **Ambiguous risk level:** Present both possible classifications with reasoning. Flag for legal review.
- **Deployer may be provider:** If Art. 25 triggers are detected, alert the user prominently.
- **Dual classification:** An AI system can be both high-risk AND transparency-obligated. Present all applicable layers.
- **Out of scope:** If the system falls outside Art. 2, explain why and note which law may still apply (GDPR, product safety, etc.).
