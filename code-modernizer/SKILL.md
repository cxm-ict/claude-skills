---
name: code-modernizer
description: Analyzes and modernizes legacy code projects using a two-phase approach. Use this skill whenever the user wants to modernize, refactor, or upgrade an existing codebase. Activate when the user mentions old code, legacy projects, outdated dependencies, technical debt, refactoring, or upgrading a codebase to modern standards. Always run Phase 1 analysis first and wait for explicit user approval before touching any files.
---

# Code Modernizer

A Claude Code skill that analyzes legacy code and modernizes it using current best practices.

**Approach:** Two phases. Analyze first. Build only after explicit user approval.
**Output:** A modernized copy of the project in a `/modernized` folder. The original is never modified.

---

## Requirements

- Claude Code (does not work in Claude.ai)
- A Pro or Max subscription (analyzing and rewriting a full codebase is token-intensive)
- The project folder must be accessible from your terminal
- Git installed (recommended for safe rollback)

---

## Supported languages

- JavaScript and TypeScript
- Python
- PHP
- Java
- HTML and CSS (when part of a code project)

Other languages: the skill will attempt analysis but will flag uncertainty clearly and explicitly.

---

## Phase 1: Analysis

Run this phase first. Do not modify any files. Do not create any files except the analysis report.

### What to analyze

**Project overview**
- What does this project do?
- What language(s) and version(s) are used?
- What is the folder structure?
- What dependencies are present and what versions?
- What external services, databases, or APIs does this project connect to?

**File hygiene**
- Are there encoding issues? Check for BOM markers, mixed line endings (CRLF vs LF), or non-UTF-8 encoding. List every affected file.
- Are there configuration files present that need modernization? Check for .htaccess, web.config, webpack.config.js, .babelrc, Gruntfile, Gulpfile, and similar.

**Code health**
- What patterns are outdated and why?
- What parts of the code are most fragile or hardest to maintain?
- Are there obvious bugs or anti-patterns?
- Is there dead code (functions, classes, or modules that are never called)? List every instance.
- Are there outdated or misleading comments that describe behavior incorrectly? List every instance.
- Are there performance issues that can be addressed without architectural changes? Examples: N+1 queries, synchronous calls that can be made async, repeated computations that can be cached.

**Security findings**
- Are there hardcoded credentials, API keys, or secrets anywhere in the codebase? List every instance with the file and line number.
- Are there SQL injection risks?
- Are there XSS vulnerabilities?
- Is user input validated and sanitized?
- Are there insecure dependencies with known CVEs?
- Are there insecure cryptographic practices (MD5, SHA1 for passwords, weak random number generation)?

**Dependency audit**
- Which dependencies are outdated? List current version and latest stable version.
- Which dependencies have known vulnerabilities? List the CVE identifiers where available.
- Which dependencies can be replaced with native language features?
- Which dependencies are no longer maintained (no commits in 2 years or officially deprecated)?
- What is the license of each dependency? Flag any licenses that may be incompatible with commercial use (GPL, AGPL, SSPL). This is not legal advice. Flag and let the user decide.

**External services and integrations**
- List every external service, API, or database this project connects to.
- Flag any connections that may break after modernization (changed library interfaces, new authentication patterns, deprecated API versions).
- These cannot be automatically fixed. They require manual review after modernization.

**Test coverage**
- Are there existing tests? If so, what do they cover and how reliable do they appear?
- Where are tests missing entirely?
- Are existing tests brittle (testing implementation rather than behavior)?

**Breaking changes assessment**
- List every change in the proposed modernization that could affect external behavior.
- This includes: changed function signatures, renamed exports, changed response formats, modified configuration structures, changed file locations.
- Mark each one as BREAKING or NON-BREAKING.

**Modernization plan**
- List every proposed change per file or module.
- Assign a risk level to each change: LOW, MEDIUM, or HIGH.
- Explain the reason for each change in one sentence.
- List explicitly what will NOT be touched and why.
- Provide an overall complexity estimate: LOW, MEDIUM, or HIGH.

### Recommendation

Based on all findings, provide one of three recommendations:

**PROCEED** The modernization is safe and the benefits are clear.

**PROCEED WITH CAUTION** The modernization is valuable but contains HIGH risk changes that require extra attention. List them explicitly.

**DO NOT PROCEED** The risk outweighs the benefit. Explain clearly why. Do not soften this. If the codebase is too fragile, too deeply coupled to deprecated systems, or too risky to touch without a full rewrite, say so directly.

### Analysis output

Write the full analysis to `MODERNIZATION-REPORT.md` in the project root.

Structure the report as follows:

```
# Modernization Report

## Project summary
## Language and version
## File hygiene findings
## Code health findings
## Security findings (CRITICAL items at the top)
## Dead code inventory
## Outdated comments inventory
## Performance quick wins
## Dependency audit
## License flags (if any)
## External services and integration risks
## Test coverage
## Breaking changes (marked BREAKING or NON-BREAKING)
## Proposed changes per file (with risk level and reason)
## What will NOT be changed and why
## Overall complexity: LOW / MEDIUM / HIGH
## Recommendation: PROCEED / PROCEED WITH CAUTION / DO NOT PROCEED
```

### Stop here

After writing the report, stop completely. Print this message:

```
Analysis complete. Report saved to MODERNIZATION-REPORT.md.

Please read the full report before continuing. Pay special attention to:
- Security findings
- Breaking changes
- External service risks
- License flags

Type PROCEED to start the modernization, or ask questions about the findings first.
```

Do not start Phase 2 until the user types PROCEED.

---

## Phase 2: Modernization

Only start this phase after the user has explicitly typed PROCEED.

### Rules

- Never modify the original files
- Create a `/modernized` folder in the project root
- Replicate the original folder structure inside `/modernized`
- Apply all proposed changes from the report
- Skip any changes the user has explicitly asked to exclude
- If you encounter something unexpected that was not in the report, stop and ask before proceeding

### Rollback preparation

Before writing a single file, print this message:

```
Before I start, I recommend creating a git commit of your current state as a safety net.

If you have git initialized, run:
  git add .
  git commit -m "snapshot before code-modernizer"

If you do not use git, make a manual copy of your project folder now.

Type READY when you want me to continue.
```

Wait for the user to type READY before proceeding.

### What to do per file

**File hygiene first**
- Normalize all line endings to LF
- Remove BOM markers
- Convert non-UTF-8 files to UTF-8
- Document every file where encoding was changed in CHANGES.md

**JavaScript and TypeScript**
- Upgrade to modern syntax: const/let, arrow functions, async/await, optional chaining, nullish coalescing
- Replace var with const or let
- Add TypeScript types if the project is being upgraded to TypeScript
- Replace outdated libraries with modern alternatives or native equivalents
- Remove unused imports and dead code
- Fix outdated or misleading comments

**Python**
- Upgrade to Python 3 patterns if the project uses Python 2 syntax
- Use f-strings instead of % or .format()
- Replace deprecated standard library calls
- Add type hints where missing
- Use pathlib instead of os.path where appropriate
- Fix outdated or misleading comments

**PHP**
- Replace deprecated functions
- Apply modern PHP 8 syntax where applicable
- Replace MySQL extension with PDO or MySQLi
- Add input validation and output escaping where missing
- Fix outdated or misleading comments

**Java**
- Upgrade to modern Java patterns: streams, lambdas, var keyword
- Replace deprecated APIs
- Apply modern exception handling patterns
- Fix outdated or misleading comments

**All languages**
- Replace hardcoded credentials or secrets with environment variable references
- Document every replaced secret in `.env.example` with: the variable name, what it is, where to get the value, and whether it is required or optional
- Remove all dead code. Add a comment in CHANGES.md for every removed block so the user knows what was deleted.
- Apply performance quick wins identified in the report
- Add a comment at the top of each modified file: `// Modernized by code-modernizer skill. Review before deploying.`

**Configuration files**
- Modernize .htaccess, webpack.config.js, .babelrc, and similar files where identified in the report
- Document every configuration change in CHANGES.md

### Breaking changes

For every change marked BREAKING in the report, add a prominent comment in the code directly above the changed line:

```
// BREAKING CHANGE: [what changed and what callers need to update]
```

Also collect all breaking changes in a dedicated `BREAKING-CHANGES.md` file in `/modernized`. This file must be read before deploying.

### Tests

- If existing tests are present: copy them to `/modernized` and update them to match the new code
- Where tests are missing: generate example tests and save them to `/modernized/tests-to-review/`
- Mark every generated test with a comment: `// GENERATED. Review and validate before using in production.`
- Do not claim these tests are complete or correct. They are a starting point only.

### After modernization

**Write CHANGES.md inside `/modernized`**

Structure:

```
# Changes

## Files modified (with reason per change)
## Dead code removed (list every removed block)
## Dependencies replaced (old package, new package, reason)
## Security issues addressed
## Encoding changes
## Configuration files updated
## Breaking changes (summary, full list in BREAKING-CHANGES.md)
## Generated tests (location, what they cover, review required)
## What was intentionally left unchanged and why
## External services requiring manual review (list from report)
```

**Write COMPARISON.md inside `/modernized`**

This is the before/after report. Include:

- Total files analyzed
- Total files modified
- Lines of code before vs after
- Number of outdated dependencies found vs replaced
- Number of security issues found vs addressed
- Number of dead code blocks removed
- Number of encoding issues fixed
- Number of breaking changes introduced
- Number of generated tests created
- Overall assessment: is the modernized version meaningfully better? Be honest. If the gains are marginal, say so.

Then print this message:

```
Modernization complete.

Your original code is untouched.
The modernized version is in /modernized.

Before doing anything else, read these files in order:
1. BREAKING-CHANGES.md: understand what may break
2. CHANGES.md: understand everything that changed
3. COMPARISON.md: understand the before/after picture
4. /tests-to-review/: review all generated tests before using them

Check your .env.example for any secrets that need to be configured.

If external services are listed in the report, test those connections manually.

This skill does not guarantee correctness. Always review the output before deploying.

To roll back: restore from your git snapshot or your manual backup.
```

---

## What this skill does not do

- It does not guarantee the modernized code works correctly
- It does not replace manual code review
- It does not write production-ready tests
- It does not handle database migrations or schema changes
- It does not update infrastructure or deployment configuration
- It does not make architectural decisions without asking
- It does not provide legal advice on licenses
- It does not fix broken integrations with external services automatically
- It does not guarantee that breaking changes are complete. There may be callers or consumers not visible in this codebase.

If any of the above are needed, the skill flags this in the report and suggests next steps.

---

## Found something missing?

This skill is a first version. If you run it and encounter a situation it did not handle well, open an issue at the GitHub repository. That is how it gets better.

---

## Installation note

This skill requires Claude Code. It does not work in Claude.ai.

Place this file at `.claude/skills/code-modernizer/SKILL.md` in your project folder for project-specific use.

Or place it at `~/.claude/skills/code-modernizer/SKILL.md` to use it across all your projects.
