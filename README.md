# HEXIS AI Governance Plugin

**The open-source EU AI Act risk classification plugin for Claude — by HEXIS**

Classify AI systems under the EU AI Act (Regulation (EU) 2024/1689) and receive structured compliance guidance using the HEXIS ORIENT methodology.

## What it does

This plugin walks you through a complete EU AI Act compliance assessment:

- **Prohibited practices** (Article 5) — Screen for banned AI uses
- **High-risk classification** (Article 6 + Annex I/III) — Determine if your system is high-risk
- **GPAI model obligations** (Articles 51-56) — Classify general-purpose AI models
- **Transparency requirements** (Article 50) — Identify disclosure obligations
- **Obligations mapping** — Role-specific requirements (provider vs. deployer)
- **Compliance gap assessment** — Quick self-assessment checklist
- **Action priorities** — What to do first, based on your classification and deadlines

## ORIENT Framework

Every classification follows the HEXIS ORIENT methodology:

| Stage | What it does |
|-------|-------------|
| **O** — Observe | Identify system, role, and scope |
| **R** — Risk | Classify under EU AI Act risk categories |
| **I** — Identify | Map legal obligations by role |
| **E** — Evaluate | Assess current compliance gaps |
| **N** — Navigate | Chart path from findings to action |
| **T** — Track | Set deadlines and review triggers |

Most tools stop at **R**. This plugin delivers the full cycle.

## Quick Start

### Install in Claude Cowork

1. Open Cowork → Plugins → "+"
2. Add from GitHub: `hexis-ai/hexis-ai-governance`

### Install in Claude Code

```bash
claude plugin add hexis-ai/hexis-ai-governance
```

### Use

**Option A — Slash command:**
```
/hexis:risk-classify ML-based credit scoring model used by a German bank
```

**Option B — Natural language:**
> "Classify my AI chatbot under the EU AI Act"
> "Is my recruitment screening tool high-risk?"
> "What EU AI Act obligations apply to my emotion recognition system?"

Claude will automatically activate the skill when your question matches.

## Example Output

```
## EU AI Act Risk Classification Report
Generated using the HEXIS ORIENT Framework

### OBSERVE — System Profile
- System: ML-based credit scoring model
- Role: Deployer
- EU nexus: Bank established in Germany
- Scope: In scope (Art. 2(1)(a))

### RISK — Classification
- Prohibited (Art. 5): None identified
- High-risk (Art. 6): HIGH-RISK — Annex III, Area 5(b) (creditworthiness)
- Art. 6(3) exception: Not available — profiling override applies
- Transparency (Art. 50): Art. 50(1) — AI interaction disclosure

### IDENTIFY — Key Obligations
[Deployer obligations with article references...]

### EVALUATE — Compliance Quick-Assessment
[Checklist items...]

### NAVIGATE — Recommended First Steps
1. Conduct FRIA (Art. 27) — required for creditworthiness
2. Assign trained human oversight staff (Art. 26(2))
...

### TRACK — Timeline
- Deadline: 2 August 2026
- Review triggers: model update, data source change, scope expansion
```

## Enforcement Timeline

| Date | What applies |
|------|-------------|
| Feb 2025 | Prohibited practices (Art. 5) + AI literacy (Art. 4) — **IN FORCE** |
| Aug 2025 | GPAI (Arts. 51-56) + Transparency (Art. 50) — **IN FORCE** |
| Aug 2026 | High-risk Annex III systems |
| Aug 2027 | High-risk Annex I (safety components in regulated products) |

## Plugin Structure

```
hexis-ai-governance/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── risk-classify.md
├── skills/
│   └── eu-ai-act-risk-classification/
│       └── SKILL.md
├── README.md
├── LICENSE
└── CHANGELOG.md
```

## Modules Roadmap

### Available Now (v0.2.1)
- ✅ EU AI Act Risk Classifier

### Coming Soon
- 🔲 Compliance Documenter — FRIA templates, technical documentation, conformity assessment guidance
- 🔲 AI Literacy Assessor — Article 4 obligation assessment and training plans
- 🔲 Continuous Monitor — Ongoing compliance tracking and audit support

### Future Add-ons
- 🔲 KVKK (Turkish Data Protection) crosswalk
- 🔲 NIST AI RMF mapper
- 🔲 Brazil LGPD-AI module

## Legal References

- **Primary:** EU AI Act — Regulation (EU) 2024/1689
- **Supporting:** ISO/IEC 42001:2023, ISO/IEC 22989:2022, ISO/IEC 23894:2023
- **Complementary:** NIST AI RMF 1.0, OECD AI Principles

## Disclaimer

This plugin provides compliance orientation and is not legal advice. Always consult qualified legal counsel for binding compliance decisions. Classification outputs reflect the EU AI Act as published, including known proposed amendments (Digital Omnibus COM/2025/837) where flagged.

## Contributing

Contributions welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

Apache 2.0 — see [LICENSE](LICENSE).

## About HEXIS

HEXIS AI Governance provides human-centered AI compliance tools and methodology. The ORIENT framework transforms regulatory complexity into structured, actionable guidance.

Learn more: [hexis.center](https://hexis.center)
