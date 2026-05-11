# Changelog

## Meeting-to-action

### v1: May 2026

Initial release.

**Input types supported:**
- Typed notes or transcripts
- Voice memo transcripts
- Descriptions of what was discussed
- PDF exports from a Remarkable tablet
- Photos of handwritten notes from any source (notebook, whiteboard, tablet, phone)

**Phase 1 reads the input:**
- Automatic detection of input type
- Transcription of handwritten notes with [?] flags for illegible parts
- Confirmation step before report generation for handwritten input

**Phase 2 asks clarifying questions:**
- Always asks language (Dutch or English) and output format (PDF, DOCX, MD)
- Asks only what is missing from the input
- Optional questions for confidentiality, approval, references, and next meeting

**Phase 3 builds the report:**
- Self-explanatory summary for both attendees and absentees
- Decisions section with only confirmed outcomes
- Action points in a table with owner and deadline
- Open questions for unresolved items
- Next meeting section
- References section
- Approval section for organizations with formal sign-off
- Confidentiality notice when applicable
- Version number and date

**Output formats:**
- Markdown (MD)
- Word document (DOCX) with proper table formatting
- PDF

**Rules:**
- Action points must be concrete with named owner and deadline
- Decisions must be final
- Never invent information, mark gaps with [?]
- No em-dashes
- Tone is direct and professional

**License:** CC BY-NC-SA 4.0

---

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

### May 2026

- Added Meeting-to-action skill to the repository
- README updated with installation steps for Claude.ai skills

### April 2026

- License changed from MIT to CC BY-NC-SA 4.0
- GETTING-STARTED.md updated with Claude Desktop installation steps
