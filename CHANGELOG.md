# Changelog

All notable changes to the HEXIS AI Governance plugin will be documented in this file.

## [0.2.0] - 2026-02-25

### Fixed — Full Legal Audit
- **Art. 3 definition numbering (CRITICAL):** Provider corrected from Art. 3(8) to Art. 3(3), Importer from Art. 3(9) to Art. 3(6), Distributor from Art. 3(10) to Art. 3(7) — both in role identification and key definitions sections
- Key Definitions section expanded: added Importer and Distributor entries with correct Art. 3 references

### Added
- Art. 55 citation for GPAI systemic risk obligations (was described but uncited)
- Art. 71 reference for EU database (alongside existing Art. 49 registration reference)
- Art. 4 AI literacy provision in IDENTIFY stage — applies to ALL operators regardless of risk level, in force since Feb 2025

### Verified Correct (no change needed)
- Art. 99(3)(4)(5)(6) penalty amounts and sub-paragraphs
- Art. 26 deployer obligation sub-paragraphs (1)(2)(4)(5)(6)(9)(11)
- Art. 5(1)(a)-(h) prohibited practices
- Art. 6(1)(2)(3) high-risk classification paths
- Art. 50(1)-(4) transparency obligations
- All Annex references (I/III/IV/VI/VII/X/XI/XII/XIII)
- FLOPS thresholds (10²³ indicative, 10²⁵ systemic risk)
- Enforcement timeline dates
- Digital Omnibus status

## [0.1.1] - 2026-02-25

### Fixed
- Art. 6(1) high-risk conditions: Corrected from "ALL three" to "BOTH conditions" (safety component + third-party conformity assessment)
- Art. 73 serious incident reporting: Fixed from "within 72 hours" to "immediately after causal link established, max 15 days after awareness"
- Art. 50(1) transparency: Added deployer cooperation obligation ("deployers must cooperate in implementation")
- Annex III 5(c): Corrected from "life/health insurance risk/pricing" to "life/health insurance risk assessment and pricing"

## [0.1.0] - 2026-02-25

### Added
- EU AI Act Risk Classification skill (`eu-ai-act-risk-classification`)
- `/hexis:risk-classify` slash command with guided interview flow
- Full ORIENT methodology integration (Observe → Risk-assess → Identify → Evaluate → Normalize → Track)
- Prohibited practices screening (Article 5 — all 8 categories with exceptions)
- High-risk classification (Article 6 + Annex I/III — both paths with Art. 6(3) exception logic)
- GPAI model classification (Articles 51-56 — including systemic risk threshold)
- Transparency obligations mapping (Article 50 — 5 obligation types)
- Role-specific obligations matrix (provider vs. deployer)
- Compliance gap quick-assessment checklist
- Prioritised action recommendations by classification
- Enforcement timeline with Digital Omnibus status tracking
- Art. 25 provider status trigger for deployer reclassification
- Profiling override for Art. 6(3) exception
- Plugin manifest, README, and LICENSE
