# Changelog

## n8n Workflow Builder

### v1: April 2026

Initial release.

**Input types supported:**
- Plain text description
- Business plan or document
- Process diagram or whiteboard photo
- Existing n8n JSON (analyze, advise, extend)

**Analysis phase covers:**
- All systems and integrations detected automatically (30+ services)
- Four mandatory questions with hard stop if unanswered
- Subworkflow recommendation for complex workflows
- Idempotency risk detection
- Volume and throttling assessment
- GDPR flag for personal data
- n8n execution limit warnings
- Webhook security check (always required)
- Timezone mismatch detection
- Binary data handling flag
- Webhook response strategy (sync vs async)
- Environment strategy (test vs production)
- Assumptions documented before building

**Build phase produces:**
- Importable n8n JSON with versioned sticky note and changelog
- Input validation node after every trigger
- Webhook authentication always configured
- Pagination loop for API calls that return multiple pages
- Timezone normalization where needed
- Error Trigger with compensating actions on error path
- Subworkflow JSONs generated separately when needed
- Environment variable placeholders with ENV_ prefix
- Mermaid flowchart matching JSON structure exactly
- Markdown documentation with test data examples

**25 common mistakes actively prevented:**
Triggers and input, logic and data, execution patterns, technical limits, maintenance and compliance.

**License:** CC BY-NC-SA 4.0

---

## Code Modernizer

### v1: April 2026

Initial release. Two-phase approach with mandatory PROCEED approval. Original files never modified. Full analysis report with security findings, dead code, license flags, breaking changes, and rollback instructions.

---

## Website Builder

### v3: April 2026

Three-phase build: Foundation, Parallel, Assembly. Agent 2 and Agent 4 run simultaneously. CONTENT-PLAN.md as shared reference. Removed all em-dashes.

### v2: April 2026

Added color, font, visual style, language, and business plan as variables. Three image strategies. Expanded security and DEPLOY.md.

### v1: April 2026

Initial release. Four agents in sequence. Stack: Next.js with Tailwind CSS.

---

## VA-light

### v2: April 2026

Added language, typical recipients, and working days as variables. Translated to English for international use.

### v1: April 2026

Initial release. Personal assistant mode for daily professional tasks.

---

## Repository

### April 2026

- License changed from MIT to CC BY-NC-SA 4.0
- GETTING-STARTED.md updated with Claude Desktop installation steps
