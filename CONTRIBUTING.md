# Contributing to HEXIS AI Governance Plugin

Thank you for your interest in contributing to the HEXIS AI Governance plugin. This project aims to make EU AI Act compliance accessible through open-source tooling.

## How to Contribute

### Reporting Issues

- Use [GitHub Issues](https://github.com/hexis-ai/hexis-ai-governance/issues) for bug reports and feature requests
- For legal accuracy issues (wrong article references, outdated provisions), please label with `legal-accuracy`
- Include the SKILL.md line number and the correct EU AI Act reference when reporting legal errors

### Legal Accuracy Standards

This is a compliance tool. Legal precision matters. When contributing:

- Always cite article numbers: `Article 6(1)(a) Regulation (EU) 2024/1689`
- Include Recital references where they clarify interpretation
- Distinguish between current law and proposed amendments (e.g., Digital Omnibus)
- Flag where interpretation is debatable — compliance tools should not present contested interpretations as settled
- Reference the Official Journal text (EUR-Lex), not secondary sources

### Submitting Changes

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test with at least 3 scenarios (high-risk, low-risk, edge case)
5. Update CHANGELOG.md with your changes
6. Submit a pull request with:
   - Description of changes
   - Legal references for any regulatory content changes
   - Test scenarios and results

### Code of Conduct

- Be respectful and constructive
- Prioritise accuracy over speed
- When in doubt about a legal interpretation, flag it rather than guessing

### Areas Where Help is Needed

- **Translations:** Plugin UI strings for EU languages
- **Test scenarios:** Real-world edge cases across industries
- **Jurisdiction modules:** KVKK, NIST AI RMF, LGPD-AI add-ons (see roadmap in README)
- **Harmonised standards:** Updates as EN standards are published under the AI Act
- **Commission guidelines:** Integration of new guidance as the AI Office publishes it

### Licensing

By contributing, you agree that your contributions will be licensed under the Apache 2.0 License.

## Questions?

- Open an issue for technical questions
- Visit [hexis.center](https://hexis.center) for methodology questions about the ORIENT framework
