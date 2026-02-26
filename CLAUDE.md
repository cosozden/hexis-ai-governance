# HEXIS AI Governance — Claude Code Project Context

> **Read this file at the start of EVERY session.** It ensures brand, design, terminology, and quality consistency across all outputs.

---

## 1. Project Identity

**Project:** HEXIS AI Governance Compliance Plugin
**Repo:** github.com/cosozden/hexis-ai-governance
**Current Version:** 0.2.1
**License:** Apache 2.0
**Founder:** Özden — ISO/IEC 42001 Lead Implementer, preparing for IAPP AIGP exam
**Web:** hexis.center

**Language Policy:**
- All user-facing outputs (plugin files, README, commands, docs): **English only**
- Internal notes, project management: Turkish OK
- Technical/legal terms always in English

**Brand Voice:**
- Clear, authoritative, practical — no hype
- "Compliance as orientation, not checklist" (ἕξις — Hexis)
- McKinsey report aesthetic — minimal, corporate, substance over style
- Never use "revolutionary", "game-changing", "cutting-edge" or similar AI hype language

---

## 2. ORIENT Framework (v0.2.1) — CRITICAL REFERENCE

The HEXIS normative methodology. Use these exact terms in ALL outputs.

| Letter | Stage | Description |
|--------|-------|-------------|
| **O** | **Observe** | Identify the AI system, role, and context |
| **R** | **Risk** | Classify risk level per EU AI Act |
| **I** | **Identify** | Map applicable legal obligations |
| **E** | **Evaluate** | Assess current compliance gaps |
| **N** | **Navigate** | Chart path from findings to action |
| **T** | **Track** | Set deadlines and review triggers |

### Output Format Headers
```
### OBSERVE — System Profile
### RISK — Classification
### IDENTIFY — Applicable Obligations
### EVALUATE — Compliance Quick-Assessment
### NAVIGATE — Recommended First Steps
### TRACK — Timeline & Review Triggers
```

### DEPRECATED TERMS — NEVER USE
| OLD (forbidden) | NEW (required) |
|-----------------|----------------|
| ~~Risk-Assess~~ | **Risk** |
| ~~Normalize~~ | **Navigate** |
| ~~Implement~~ (as ORIENT stage name) | **Identify** |
| ~~Evidence~~ (as ORIENT stage name) | **Evaluate** |

Note: "implement" and "evidence" as regular English verbs in action items are fine (e.g., "Implement human oversight"). They are only forbidden as ORIENT stage names.

---

## 3. Visual Design System

### Color Palette
| Role | Color | Hex |
|------|-------|-----|
| Background (primary) | Dark navy | `#0A1628` |
| Text (primary) | White | `#FFFFFF` |
| Accent (links, highlights) | Agate blue | `#2D6BE4` |
| ORIENT badges/labels | Amber | `#F59E0B` |
| Success/pass | Green | `#22C55E` |
| Error/prohibited | Red | `#EF4444` |

### Typography
- Headings: Bold sans-serif (Inter, system-ui fallback)
- Body: Regular weight sans-serif
- Code/technical: Monospace

### Visual Rules
- ORIENT stage labels as small badges: `● ORIENT: Risk`
- Icons: Line style, no fill
- Logo placement: Bottom-right "hexis" wordmark + "hexis.center"
- Style: Minimal, corporate — McKinsey report aesthetic
- No decorative elements unless functional

### LinkedIn Image Dimensions
- Infographic: 1080×1350px (vertical)
- Carousel slides: 1080×1080px (square)
- Video/Reels: 1080×1920px (vertical) or 1080×1080px (square)

---

## 4. EU AI Act Reference Standards

### Risk Categories (exact official terminology)
- **Prohibited** (Unacceptable risk) — Article 5
- **High-risk** — Article 6 + Annex I / Annex III
- **Limited risk** (Transparency obligations) — Article 50
- **General-purpose AI models** — Articles 51–56
- **Minimal risk** — Voluntary codes of conduct (Art. 95)

### Enforcement Timeline
| Date | What | Status |
|------|------|--------|
| 2 Feb 2025 | Prohibited practices (Art. 5) + AI literacy (Art. 4) | **In force** |
| 2 Aug 2025 | GPAI obligations (Chapter V) | **In force** |
| 2 Aug 2026 | High-risk systems — Annex III | Upcoming |
| 2 Aug 2027 | High-risk systems — Annex I (product safety) | Upcoming |

### Digital Omnibus (proposed Nov 2025)
- **Status:** Under ordinary legislative procedure — NOT YET ADOPTED
- **If adopted:** May extend Annex III deadline to max 2 Dec 2027, Annex I to max 2 Aug 2028
- **AI literacy:** Proposal may shift responsibility from providers/deployers to Commission/Member States
- Always flag as uncertain: "Digital Omnibus (proposed): If adopted, may extend deadlines — monitor status"

### Key Penalties
- Prohibited violations: €35M or 7% global turnover (Art. 99(3))
- High-risk violations: €15M or 3% global turnover (Art. 99(4))
- Incorrect information: €7.5M or 1% (Art. 99(5))

### Citation Format
Always cite with article numbers: "Article 6(1)(a) Regulation (EU) 2024/1689"

### Reference Sources
- **Primary:** EU AI Act — Regulation (EU) 2024/1689 (EUR-Lex)
- **Supporting:** ISO/IEC 42001:2023, ISO/IEC 22989:2022, ISO/IEC 23894:2023
- **Complementary:** NIST AI RMF 1.0, OECD AI Principles
- **Verification:** artificialintelligenceact.eu, euaiact.com

---

## 5. Plugin File Structure

```
hexis-ai-governance/
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── commands/
│   └── risk-classify.md
├── skills/
│   └── eu-ai-act-risk-classification/
│       └── SKILL.md
├── CLAUDE.md          ← this file
├── README.md
├── LICENSE
└── CHANGELOG.md
```

### Version Sync Rule
When version changes, update ALL of these:
1. `plugin.json` → `"version": "X.Y.Z"`
2. `CHANGELOG.md` → New entry
3. `README.md` → If version-specific content exists
4. Git tag → `vX.Y.Z`

---

## 6. Quality Assurance — 3 Phase Protocol

**Every HEXIS output must pass this protocol before release.**

### Phase 1 — Functional Test
- ORIENT terminology correct? (6 stages, correct names)
- Decision tree produces correct classification?
- 3+ test scenarios: expected use, edge case, minimal/negative
- Version numbers consistent across all files?
- No deprecated terminology (Risk-Assess, Normalize)?

### Phase 2 — Source Verification
- **CRITICAL: Never trust memory for legal references**
- Every article number, date, penalty amount → verify via web search
- Minimum 2 independent sources per reference
- Flag interpretation uncertainty explicitly

### Phase 3 — Structural Integrity
- Brand voice consistent?
- File structure correct?
- Cross-references updated? (one file changes → all referencing files updated)
- CHANGELOG reflects changes?

---

## 7. Code Safety Rules

| Risk Level | Description | Action |
|------------|-------------|--------|
| 🟢 LOW | Read, display, calculate | Proceed |
| 🟡 MEDIUM | File create, pip install, network | Inform user |
| 🔴 HIGH | rm, chmod, git push --force, credentials | STOP + ask permission |
| ⛔ CRITICAL | Wildcard delete, system files, plaintext API keys | FORBIDDEN — offer alternative |

**Before every destructive command:**
1. `pwd` to verify location
2. Never use wildcards with rm/mv
3. Explain what the command will do
4. Wait for confirmation

---

## 8. Sprint Status

**Sprint 1 (Risk Classifier MVP):** ✅ COMPLETE (v0.2.1)
**Sprint 2 (Compliance Documenter):** NEXT
- FRIA template generator (Art. 27)
- Technical documentation template (Art. 11 + Annex IV)
- Conformity assessment guidance (Art. 43)
- Post-market monitoring plan template (Art. 72)

### Sprint 2 Backlog (from QA v0.2.1)
1. Art. 73: Add death (10 days) and widespread infringement (2 days) sub-timelines
2. Digital Omnibus: Update wording with backstop dates
3. Digital Omnibus AI literacy: Flag potential responsibility shift
4. Navigate stage: Add quick wins vs structural changes, resource allocation, stakeholder communication

---

## 9. LinkedIn Content Defaults

When generating LinkedIn content for HEXIS:
- Tag relevant ORIENT stage
- Include Claude Code visual prompt at end
- Hashtags: #EUAIAct #AIGovernance #AICompliance #RiskClassification #OpenSource #HEXIS #ORIENT #RegTech
- Hook must be 5x stronger than rest of content
- Always include "save value" — reader should want to bookmark
- Language: Default English for global audience; Turkish posts are separate

---

## 10. Session Start Checklist

At the beginning of each Claude Code session:

1. ✅ Read this CLAUDE.md
2. ✅ Confirm which sprint/task we're working on
3. ✅ Check current version in plugin.json
4. ✅ Verify ORIENT terminology is v0.2.1 (Navigate, not Normalize)
5. ✅ Ask if there are new decisions from claude.ai sessions to incorporate
