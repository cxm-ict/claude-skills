# Claude Skills

Free, ready-to-use skills for Claude, built for daily professional use.

No prompt engineering. No technical knowledge required. Download a skill, install it, and Claude works the way you work.

---

## What is a skill?

A skill is a small instruction file that teaches Claude how to handle specific tasks, in your tone, your language, and your style. You install it once. Claude picks it up automatically whenever it's relevant.

Think of it as onboarding a new colleague. You explain how things work once. After that, they just know.

---

## Available skills

### Meeting-to-action: From notes to structured report
Turns raw meeting input into a clean, structured report ready to send.

Accepts: typed notes, voice memo transcripts, PDFs from a Remarkable tablet, or photos of handwritten notes from any source (notebook, whiteboard, tablet, phone).

Output: PDF, Word document (DOCX), or Markdown. Includes summary, decisions, action points with owner and deadline, open questions, next meeting, references, and approval section.

Works for both attendees and absentees. Asks only what is missing from your input.

Works in: Claude.ai and Claude Desktop

👉 [Download Meeting-to-action](meeting-to-action/SKILL.md)

---

### VA-light: Personal Assistant
Claude acts as a lightweight personal assistant for your daily professional tasks.

Handles: email writing, summarizing, meeting prep, meeting debrief, feedback, LinkedIn posts, task prioritization, and client communication.

Works in: Claude.ai and Claude Desktop

👉 [Download VA-light](va-light/SKILL.md)

---

### Website Builder: Multi-Agent
Four specialized agents build a complete, professional website from scratch.

Agent 1 builds the structure. Agent 2 writes the content. Agent 3 handles all design and styling. Agent 4 covers SEO, security, and deployment.

Supports: business plan as input, custom brand colors, contact forms, Google Analytics, newsletter signup, and step-by-step deployment instructions.

Stack: Next.js + Tailwind CSS

Requires: Claude Code and a Pro or Max subscription.

👉 [Download Website Builder](website-builder/SKILL.md)

---

### Code Modernizer
Analyzes a legacy codebase and modernizes it using current best practices.

Phase 1 produces a full analysis report: code health, security findings, dead code, outdated dependencies, license flags, breaking changes, and a recommendation. Phase 2 builds a modernized copy only after explicit approval.

The original code is never modified.

Supports: JavaScript, TypeScript, Python, PHP, Java, HTML and CSS.

Requires: Claude Code and a Pro or Max subscription.

👉 [Download Code Modernizer](code-modernizer/SKILL.md)

---

### n8n Workflow Builder
Turns any process description into a production-ready n8n workflow.

Accepts: plain text, business plans, process diagrams, whiteboard photos, or existing n8n JSON. Always analyzes first, builds only after explicit approval.

Output: importable n8n JSON, Mermaid diagram, and Markdown documentation.

Built on 15+ years of real-world automation experience. Covers 25 common n8n mistakes actively, including idempotency, webhook security, pagination, GDPR, error handling, compensating actions, and versioning.

Works in: Claude.ai and Claude Code

👉 [Download n8n Workflow Builder](n8n-workflow-builder/SKILL.md)

---

### Promptmaker: From vague question to ready-to-use prompt
A quick interviewer that turns a vague or half-formed request into one sharp, copy-paste-ready prompt.

Works from four building blocks: context, goal, constraints, and example. Asks only what is missing, never more than four questions, bundled in one turn. If your request is already complete, it skips the interview and builds straight away.

Output: the finished prompt in a separate copyable block, in the language of the use case, plus a short explanation of why it works.

Works in: Claude.ai and Claude Desktop

👉 [Download Promptmaker](promptmaker/SKILL.md)

---

### Prompt-architect: Reusable, tested prompt assets
The heavy version of Promptmaker. Builds a prompt asset instead of a one-off: domain-specific, tested against real output, refined, and made reusable with variables.

Runs in four phases and uses two reference files (domains and techniques). Applies professional build techniques: role, examples, structure, and success criteria. The quality loop is mandatory, an untested prompt is not an asset.

Best for recurring professional work: client communication, cold outreach, content marketing, technical specs, analysis, and customer service.

Output: a reusable template with clearly marked variables.

Works in: Claude Code and Claude.ai

👉 [Download Prompt-architect](prompt-architect/SKILL.md)

---

## How to install a skill

**For Meeting-to-action, Promptmaker, and VA-light (Claude.ai or Claude Desktop):**
1. Download the SKILL.md file
2. Go to Settings > Customize > Skills
3. Click the + button and upload the file
4. Toggle it on

**For Website Builder, Code Modernizer, n8n Workflow Builder, and Prompt-architect (Claude Code or Claude.ai):**
1. Download the SKILL.md file
2. Open it and replace the fields between [ ] with your own details if needed
3. Place the file at `.claude/skills/[skill-name]/SKILL.md` in your project folder
4. Run Claude Code in your project folder

For full installation instructions, see [GETTING-STARTED.md](GETTING-STARTED.md).

---

## More skills coming

This repository is updated regularly with new skills for professionals.

Follow along or check back for updates. Found something missing? Open an issue.

---

## License

CC BY-NC-SA 4.0, free to use and adapt for non-commercial purposes. Attribution required. Commercial use is not permitted without written permission.

Contact: michael@cxm-ict.com

---

Built by [Michael Doomen](https://www.linkedin.com/in/michaeldoomen) at [CXM-ICT](https://cxm-ict.com)
