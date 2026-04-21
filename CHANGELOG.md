# Changelog

## Code Modernizer

### v1: April 2026

Initial release.

Two-phase approach: analysis first, modernization only after explicit PROCEED approval.

**Phase 1 analysis covers:**
- Project overview and language detection
- File hygiene: encoding issues, BOM markers, line endings
- Code health: outdated patterns, anti-patterns, dead code, misleading comments
- Security findings: hardcoded secrets, injection risks, insecure cryptography
- Dependency audit: outdated versions, known CVEs, unmaintained packages
- License check: flags potentially incompatible licenses for commercial use
- External services and integration risks
- Test coverage assessment
- Breaking changes assessment per proposed change
- Recommendation: PROCEED, PROCEED WITH CAUTION, or DO NOT PROCEED

**Phase 2 modernization covers:**
- File encoding normalization (UTF-8, LF line endings, BOM removal)
- Language-specific modernization for JavaScript, TypeScript, Python, PHP, Java
- Dead code removal with full inventory in CHANGES.md
- Outdated comment correction
- Secret replacement with environment variables and .env.example documentation
- Performance quick wins
- Configuration file modernization
- Breaking changes marked in code and collected in BREAKING-CHANGES.md
- Generated tests in /tests-to-review/ with explicit review-required markers
- CHANGES.md with full inventory of every modification
- COMPARISON.md with before/after metrics

**Safety features:**
- Original files are never modified
- Git snapshot recommended before Phase 2 (READY confirmation required)
- Rollback instructions included
- Explicit list of what the skill does not do

---

## Website Builder

### v3: April 2026

- Replaced sequential chain with three-phase build: Foundation, Parallel, Assembly
- Agent 2 and Agent 4 now run simultaneously on separate files
- Agent 1 now produces CONTENT-PLAN.md as shared reference for all agents
- Strict file ownership per agent to prevent conflicts
- Removed all em-dashes from skill and added rule for generated website copy

### v2: April 2026

- Added primary and secondary color as variables
- Added font style and visual style as variables
- Added language variable
- Added business plan as optional input
- Added three image strategies: Unsplash automatic, own images, branded color blocks
- Expanded security headers to five
- Added .env.example
- Expanded DEPLOY.md

### v1: April 2026

Initial release. Four agents in sequence. Stack: Next.js with Tailwind CSS.

---

## VA-light

### v2: April 2026

- Added language, typical recipients, and working days as variables
- Translated full skill to English for international use

### v1: April 2026

Initial release. Personal assistant mode for daily professional tasks.
