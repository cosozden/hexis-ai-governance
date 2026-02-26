---
name: eu-ai-act-risk-classification
description: >
  Classify AI systems under the EU AI Act (Regulation (EU) 2024/1689) risk framework.
  Covers prohibited practices (Art. 5), high-risk systems (Art. 6, Annex I/III),
  general-purpose AI models (Arts. 51-56), transparency obligations (Art. 50),
  and minimal risk. Includes obligation mapping, enforcement timeline, and
  actionable compliance guidance using the HEXIS ORIENT methodology.
  Use when the user asks about EU AI Act risk classification, AI compliance,
  AI risk assessment, prohibited AI practices, high-risk AI systems, GPAI model
  obligations, AI Act scope, Article 6(3) exception, conformity assessment,
  FRIA, or any question about how their AI system is regulated under EU law.
---

# EU AI Act Risk Classification

This skill classifies AI systems under the EU AI Act risk framework and delivers structured compliance guidance using the HEXIS ORIENT methodology (Observe → Risk → Identify → Evaluate → Navigate → Track).

## When to use this skill

- User asks to classify an AI system under the EU AI Act
- User asks whether their AI system is high-risk, prohibited, or needs transparency measures
- User asks about EU AI Act obligations, scope, or enforcement
- User describes an AI system and wants to know what applies to them
- User mentions EU AI Act compliance, GPAI models, FRIA, conformity assessment
- User triggers the `/hexis:risk-classify` command

## How to respond

When classifying an AI system, walk through every ORIENT stage sequentially. Do NOT skip steps — the EU AI Act uses a cumulative model where multiple classifications can apply simultaneously. Present the final output in the structured ORIENT report format shown at the end of this skill.

---

## ORIENT Stage: OBSERVE

### Step 0 — Role Identification

Determine the user's role under Article 3. Obligations differ significantly by role.

Key roles:
- **Provider** (Art. 3(8)): develops the AI system or has it developed, places it on market or puts it into service under own name/trademark. Heaviest obligations.
- **Deployer** (Art. 3(4)): uses the AI system under its authority (except personal non-professional use).
- **Importer** (Art. 3(9)): places on EU market a system from a third country.
- **Distributor** (Art. 3(10)): makes system available on EU market (not provider or importer).
- **Product manufacturer**: places system as part of product under own name — treated as provider (Art. 25).

**Critical:** A deployer becomes a provider if they (Art. 25(1)):
(a) put their name/trademark on a high-risk system already on market,
(b) make a substantial modification (Recital 83: change not foreseen by original provider affecting compliance), or
(c) modify the intended purpose so the system becomes high-risk.

Ask the user: "What is your role — are you developing, deploying, importing, or distributing this AI system?"

### Step 1 — Scope Check (Article 2)

**Is it an AI system?** Article 3(1): a machine-based system designed to operate with varying levels of autonomy, that may exhibit adaptiveness after deployment, and that infers from input how to generate outputs (predictions, content, recommendations, decisions) influencing physical or virtual environments. Simple rule-based systems, basic statistics, and traditional software generally fall outside this definition (Recital 12).

**EU nexus?** In scope if ANY apply (Art. 2(1)):
- Provider/deployer/importer/distributor established or located in EU
- System placed on EU market or put into service in EU
- Third-country provider/deployer whose system's output is used in the EU (Recital 22 confirms extraterritorial reach)

**"Put into service" includes internal deployment** (Art. 3(11)): supply for first use directly to deployer or for own use. No exemption for purely internal corporate use.

**Exclusions (Art. 2):**
- Military/defence/national security — exclusively for those purposes (Art. 2(3))
- Scientific R&D — sole purpose, before market placement (Art. 2(6)); real-world testing NOT excluded
- Pre-market R&D — prior to market placement (Art. 2(8))
- Personal non-professional use (Art. 2(10))
- **Open-source AI systems** (Art. 2(12)) — EXCEPT: still in scope if high-risk (Annex I/III), prohibited (Art. 5), or transparency-obligated (Art. 50). Practical effect: the open-source exception is narrow.
- **Open-source GPAI models** (Art. 53(2)) — partial exemption from technical docs (Art. 53(1)(a)) and downstream info (Art. 53(1)(b)) only. Must still comply with copyright policy and training data summary. Does NOT apply to GPAI with systemic risk. Must meet conditions: licence allows access/use/modification/distribution, parameters publicly available, model not monetised (Recital 102).

---

## ORIENT Stage: RISK

**Note for GPAI model providers:** Steps 2 and 3 apply at the AI system level. If you are solely a GPAI model provider, your primary classification point is Step 4. Still review Steps 2-3 to understand prohibited/high-risk downstream uses — this informs your acceptable use policy (Art. 53(1)).

### Step 2 — Prohibited Practices Screen (Article 5)

**In force since 2 February 2025. Penalty: up to €35M or 7% global turnover (Art. 99(3)).**

Screen for ALL of these. If ANY match (and no valid exception applies) → PROHIBITED:

| # | Practice | Article | Exception |
|---|---------|---------|-----------|
| P1 | Subliminal/manipulative/deceptive techniques materially distorting behaviour causing significant harm | Art. 5(1)(a) | None |
| P2 | Exploiting vulnerabilities (age, disability, social/economic situation) to distort behaviour | Art. 5(1)(b) | None |
| P3 | Social scoring: evaluating/classifying persons based on social behaviour/personality leading to disproportionate detrimental treatment | Art. 5(1)(c) | None |
| P4 | Criminal risk assessment based SOLELY on profiling/personality traits | Art. 5(1)(d) | AI supporting human assessment using objective verifiable facts linked to criminal activity |
| P5 | Untargeted facial recognition database creation via scraping internet/CCTV | Art. 5(1)(e) | None |
| P6 | Emotion recognition in workplace/education | Art. 5(1)(f) | Medical or safety reasons (e.g. pilot fatigue — Recital 44) |
| P7 | Biometric categorisation to infer sensitive attributes (race, religion, sexual orientation, etc.) | Art. 5(1)(g) | Labelling/filtering lawfully acquired biometric datasets (law enforcement) |
| P8 | Real-time remote biometric identification in public spaces for law enforcement | Art. 5(1)(h) | Strictly necessary: (i) targeted victim search, (ii) preventing imminent threat to life/terrorist attack, (iii) locating suspect of serious crime. Requires prior judicial authorisation (Art. 5(3-7)) |

Even if prohibited, continue screening — other aspects of the same product/service may have separate classifications.

### Step 3 — High-Risk Classification (Article 6 + Annex I/III)

**Path A — Annex I: Safety component of regulated product (Art. 6(1))**
High-risk if ALL three conditions met:
1. AI is a safety component of a product OR is itself the product
2. Product is covered by EU harmonisation legislation in Annex I, Section A (machinery, toys, lifts, medical devices, vehicles, aviation, marine, rail, etc.)
3. Product requires third-party conformity assessment under that legislation

Annex I Section B covers additional legislation including large-scale IT systems (SIS, VIS, Eurodac, EES, ETIAS — detailed in Annex X).
Timeline: August 2027 (proposed Omnibus: long-stop August 2028).

**Path B — Annex III: Standalone high-risk use cases (Art. 6(2))**
Eight areas with subcategories:

1. **Biometrics** (where permitted): (a) remote biometric identification (excludes verification/authentication), (b) biometric categorisation by sensitive attributes, (c) emotion recognition
2. **Critical infrastructure**: (a) AI as safety component in critical digital infrastructure, road traffic, water/gas/heating/electricity (cross-ref NIS2 Directive)
3. **Education**: (a) admissions/assignment, (b) evaluating learning outcomes, (c) assessing education level/access, (d) monitoring prohibited student behaviour during tests
4. **Employment**: (a) recruitment/selection (job ads, filtering, evaluating candidates), (b) decisions on work terms, promotion, termination, task allocation, monitoring/evaluating performance
5. **Essential services**: (a) public assistance eligibility, (b) creditworthiness/credit scoring (excludes fraud detection — Recital 58), (c) life/health insurance risk/pricing, (d) emergency call classification/dispatch/triage
6. **Law enforcement** (where permitted): (a) victim risk assessment, (b) polygraphs/deception detection, (c) evidence reliability, (d) re-offending risk (not solely profiling), (e) profiling in criminal investigation
7. **Migration/border**: (a) polygraphs, (b) risk assessment of persons entering EU, (c) asylum/visa/residence application examination, (d) detecting/identifying persons (excludes travel document verification)
8. **Justice/democracy**: (a) AI assisting judicial authority in researching/applying law, alternative dispute resolution, (b) AI influencing elections/referenda/voting behaviour (excludes admin/logistical campaign tools)

Timeline: August 2026 (proposed Omnibus: long-stop December 2027).

**Art. 25 Provider Status Check** — ALWAYS ask when classifying under Annex III:
"Is this use case within the intended purpose defined by the original provider?"
If NO → user may have become a NEW PROVIDER under Art. 25(1)(c), owing full provider obligations.

**Article 6(3) Exception** — An Annex III system may be NOT high-risk if BOTH conditions are met:
- Condition 1: Does NOT pose significant risk of harm to health/safety/fundamental rights AND does not materially influence decision-making
- Condition 2: Meets at least ONE of: (a) narrow procedural task, (b) improves previously completed human activity, (c) detects patterns without replacing human assessment, (d) performs preparatory task

**PROFILING OVERRIDE:** If the system profiles natural persons (automated processing to evaluate work performance, economic situation, health, preferences, reliability, behaviour, location, movement) → ALWAYS high-risk regardless of Art. 6(3) criteria.

Provider must document the Art. 6(3) assessment before market placement and register per Art. 49(2).

### Step 4 — GPAI Model Classification (Articles 51-56)

**Is it a GPAI model?** (Art. 3(63)): significant generality, wide range of distinct tasks, can be integrated into variety of downstream systems. Indicative: training compute >10²³ FLOPs + language/image/video generation capability (Commission July 2025 guidelines).

**Systemic risk?** (Art. 51(1)):
- Automatic: cumulative training compute ≥ 10²⁵ FLOPs
- Commission designation based on Annex XIII criteria

**Obligations:**
- All GPAI: technical documentation (Annex XI), info to downstream providers (Annex XII), copyright policy, training data summary, acceptable use policy, EU authorised representative for third-country providers (Art. 54)
- Systemic risk adds: model evaluations, adversarial testing/red-teaming, serious incident tracking + AI Office reporting, cybersecurity
- Open-source partial exemption: exempt from Annex XI docs and Annex XII info (unless systemic risk). Still must comply with copyright and training data summary.
- AI Office notification (Art. 52): required without delay when systemic risk threshold met
- Code of Practice (Art. 56): adherence can demonstrate compliance; mitigating factor for fines

**Already in force since 2 August 2025.**

**For deployers/providers of AI systems built on GPAI models:** verify upstream GPAI model provider compliance, especially: Annex XII information provided? Copyright policy documented? For systemic risk models: evaluations and red-teaming in place?

### Step 5 — Transparency / Limited Risk (Article 50)

**In force since 2 August 2025.** These are CUMULATIVE with any other classification.

| Obligation | Article | Trigger | Who | Requirement |
|-----------|---------|---------|-----|-------------|
| AI interaction disclosure | 50(1) | Direct interaction with persons | Provider | Inform person of AI nature — clearly, at first interaction (unless obvious — Recital 132) |
| Output marking | 50(2) | Generating synthetic audio/image/video/text | Provider | Machine-readable format marking as AI-generated; must be robust, interoperable, reliable |
| Emotion/biometric disclosure | 50(3) | Emotion recognition or biometric categorisation | Deployer | Inform exposed persons; GDPR compliance |
| Deep fake labelling | 50(4) | Generating/manipulating deep fake content | Provider & Deployer | Disclose artificial generation |
| AI text for public interest | 50(4) | AI text published on matters of public interest | Provider & Deployer | Disclose artificial generation |

**Direct interaction vs. background operation:** Art. 50(1) applies when persons actively engage with the AI (chatbots, recommendation interfaces). Generally does NOT apply to background systems (spam filters, backend fraud detection). When in doubt, disclose.

### Step 5b — Minimal Risk

If no previous step triggered → Minimal risk. No mandatory AI Act requirements. Voluntary codes of conduct (Art. 95). GDPR, product safety, and other law still apply.

---

## ORIENT Stage: IDENTIFY

### Step 6 — Obligations Matrix

Present obligations specific to the user's role (provider vs. deployer) and classification. Use the tables below.

**Provider obligations for high-risk (Arts. 8-22):** Risk management system (Art. 9), data governance (Art. 10), technical documentation (Art. 11 + Annex IV), record-keeping (Art. 12), transparency to deployers (Art. 13), human oversight design (Art. 14), accuracy/robustness/cybersecurity (Art. 15), quality management system (Art. 17), conformity assessment (Art. 43 — internal control via Annex VI for most Annex III; notified body via Annex VII for biometric identification and Annex I), EU declaration of conformity (Art. 47), CE marking (Art. 48), EU database registration (Art. 49), post-market monitoring (Art. 72), serious incident reporting (Art. 73 — within 72 hours).

**Deployer obligations for high-risk (Arts. 26-27):** Use per instructions (Art. 26(1)), human oversight with competent staff (Art. 26(2)), input data relevance (Art. 26(4)), monitoring (Art. 26(5)), log retention min. 6 months (Art. 26(6)), FRIA (Art. 27 — required for public bodies, entities providing public services, and deployers using 5(b) creditworthiness or 5(c) insurance systems), DPIA integration (Art. 26(9)), inform affected persons (Art. 26(11)).

**Deployer upstream verification:** If deploying a third-party high-risk system, verify: CE marking (Art. 48), EU declaration of conformity (Art. 47), instructions for use provided (Art. 13), EU database registration (Art. 49), and if GPAI-based: Annex XII documentation from model provider.

**Penalties:** Prohibited practices: €35M / 7% turnover (Art. 99(3)). High-risk violations: €15M / 3% (Art. 99(4)). Incorrect information: €7.5M / 1% (Art. 99(5)). SME/startup: proportionality applies, lower amount (Art. 99(6)). EU institutions: €1.5M (prohibited) / €750K (other) (Art. 100).

---

## ORIENT Stage: EVALUATE

### Step 7 — Compliance Gap Quick-Assessment

Present a checklist appropriate to the user's classification and role. Ask the user to self-assess.

For high-risk providers — key checks:
1. ☐ Documented risk management system?
2. ☐ Training data quality/bias assessment?
3. ☐ Technical documentation per Annex IV?
4. ☐ Instructions for use provided to deployers?
5. ☐ Human oversight mechanism designed?
6. ☐ Accuracy/robustness metrics tested?
7. ☐ Conformity assessment path identified?
8. ☐ Post-market monitoring plan?

For high-risk deployers — key checks:
1. ☐ Using system per provider instructions?
2. ☐ Competent oversight persons assigned?
3. ☐ Input data quality monitored?
4. ☐ Logs retained (min. 6 months)?
5. ☐ FRIA conducted (if required)?
6. ☐ Affected persons informed?
7. ☐ Provider's CE marking and declaration verified?

Score: 6-8 = strong foundation; 4-5 = moderate gaps; 0-3 = significant gaps.

---

## ORIENT Stage: NAVIGATE

### Step 8 — Recommended First Actions

Based on classification, provide a prioritised action list:

**Prohibited:** (1) Immediately cease, (2) Assess repurposing for lawful use, (3) Document decision, (4) If on market, initiate withdrawal.

**High-risk Annex III (deadline: Aug 2026):** Priority order: (1) Establish risk management system, (2) Begin technical documentation, (3) Audit training data, (4) Implement human oversight, (5) Conduct FRIA if deployer, (6) Identify conformity assessment path, (7) Register in EU database, (8) Establish post-market monitoring.

**High-risk Annex I (deadline: Aug 2027):** Same as above with more time. Align with existing product conformity assessment. Engage notified bodies early.

**GPAI (already in force):** (1) Verify current compliance, (2) Update technical docs, (3) Ensure copyright policy documented, (4) Publish training data summary, (5) For systemic risk: validate evaluations and red-teaming.

**Limited risk (already in force):** (1) Verify AI disclosure implemented, (2) Implement output marking (Art. 50(2)), (3) For emotion recognition deployers: confirm notification active.

**Minimal risk:** No mandatory actions. Consider voluntary codes (Art. 95). Ensure GDPR/other law compliance.

---

## ORIENT Stage: TRACK

### Step 9 — Timeline and Review Triggers

Present the enforcement timeline relevant to the user's classification.

Key dates:
- Feb 2025: Prohibited practices + AI literacy — IN FORCE
- Aug 2025: GPAI + transparency — IN FORCE
- Aug 2026: High-risk Annex III
- Aug 2027: High-risk Annex I + legacy GPAI
- Aug 2030: Public deployers

**Digital Omnibus (proposed Nov 2025, not adopted):** May extend Annex III to Dec 2027 and Annex I to Aug 2028. Flag this uncertainty.

**Review triggers — re-classify when:**
- Intended purpose changes
- Substantial system modification
- Deployment geography changes
- Significant retraining on new data
- New Commission guidelines published
- Digital Omnibus adopted
- Organisational role changes (deployer → provider)

Recommended minimum review cadence: every 12 months.

---

## Output Format

Always structure the classification report using this ORIENT format:

```
## EU AI Act Risk Classification Report
*Generated using the HEXIS ORIENT Framework*

### OBSERVE — System Profile
- **System description:** [from user input]
- **Role:** [Provider / Deployer / Importer / Distributor]
- **EU nexus:** [how the system is in scope]
- **Scope status:** [In scope / Out of scope + reason]

### RISK — Classification
- **Prohibited practices (Art. 5):** [None identified / PROHIBITED — Art. 5(1)(x)]
- **High-risk (Art. 6):** [Not high-risk / HIGH-RISK — Annex [I/III], Area [X]]
- **Art. 6(3) exception:** [Not applicable / Applied — criterion (x) / Not available — profiling override]
- **GPAI model (Arts. 51-56):** [Not applicable / GPAI / GPAI with systemic risk]
- **Transparency (Art. 50):** [None / Art. 50(1)/(2)/(3)/(4) — specify]
- **Overall classification:** [PROHIBITED / HIGH-RISK / GPAI / LIMITED RISK / MINIMAL RISK]

### IDENTIFY — Applicable Obligations
[List specific obligations with article references, differentiated by role]

### EVALUATE — Compliance Quick-Assessment
[Present relevant checklist items; ask user to self-assess]

### NAVIGATE — Recommended First Steps
[Numbered priority list based on classification and urgency]

### TRACK — Timeline & Review Triggers
[Relevant enforcement deadline; specific review triggers for this system]

---
*Structured using the HEXIS ORIENT Framework — hexis.center/orient*
*Disclaimer: This classification is for compliance orientation purposes and does not constitute legal advice.*
```

## Key Definitions (Article 3)

When discussing classifications, use these definitions precisely:
- **AI system** (Art. 3(1)): machine-based, varying autonomy, may be adaptive, infers outputs from inputs
- **Provider** (Art. 3(8)): develops or commissions development, places on market under own name
- **Deployer** (Art. 3(4)): uses system under own authority
- **Placing on the market** (Art. 3(9)): first making available on EU market
- **Putting into service** (Art. 3(11)): supply for first use (includes internal deployment)
- **Intended purpose** (Art. 3(12)): use for which the system is intended by the provider
- **Substantial modification** (Art. 3(23)): change not foreseen by provider that affects compliance
- **General-purpose AI model** (Art. 3(63)): significant generality, wide range of tasks, integrable into downstream systems

## Guidelines

- Always cite article numbers (e.g., "Article 6(1)(a) Regulation (EU) 2024/1689")
- Flag when interpretation is debatable and note if Commission guidelines are pending
- Note enforcement timeline for each obligation (already in force vs. upcoming)
- Distinguish between current law and proposed Digital Omnibus changes
- Do not mix jurisdiction-specific requirements into core EU AI Act analysis
- If user's description is ambiguous, ask clarifying questions before classifying
- Present the full ORIENT report for every classification — do not skip stages
- Always include the disclaimer that this is not legal advice
