---
name: n8n-workflow-builder
description: Builds production-ready n8n workflows from any 
input: plain text descriptions, business plans, process diagrams, whiteboard photos, or existing n8n JSON. Use this skill whenever the user wants to automate something in n8n, describes a process they want to automate, shares a workflow they want to improve, or uploads a document or image describing a business process. Always run the full analysis phase first and wait for explicit user approval before generating any output.
---

# n8n Workflow Builder

A skill that turns any process description into a production-ready n8n workflow.

**Input:** Plain text, business plan, process diagram, whiteboard photo, or existing n8n JSON.
**Output:** n8n JSON (importable), Mermaid diagram, Markdown documentation.

---

## Requirements

- Claude Code or Claude.ai (this skill works in both)
- An n8n instance (self-hosted or cloud)
- Credentials for any external services involved in the workflow

---

## Phase 1: Analysis and clarification

This phase is mandatory. Do not generate any output until the analysis is complete and the user has approved the plan.

### Step 1: Read the input

Determine what type of input was provided:

**Plain text description**
Read it fully. Extract: what triggers the workflow, what steps happen, what systems are involved, what the end result should be. List everything that is clear and everything that is missing.

**Business plan or document**
Read the full document first. Extract the relevant process or automation goal. Identify: the trigger, the steps, the systems, the desired outcome, and any constraints mentioned. List gaps that need to be filled before building.

**Process diagram or whiteboard photo**
Analyze the visual carefully. Identify every step, every decision point, every system mentioned, and every arrow or flow direction. Describe what you see back to the user in plain text and ask them to confirm before proceeding.

**Existing n8n JSON**
Parse the workflow structure. Identify: what it currently does, what nodes are used, what credentials are required, where the flow splits, and what the likely intent is. Ask the user what they want to change, improve, or extend. Note the current version number for changelog purposes.

### Step 2: Identify all systems and integrations

For every system, tool, or service mentioned or implied in the input, list:
- The name of the service
- How it connects to the workflow (trigger, action, or both)
- Which n8n node handles it (built-in or community node)
- What credentials are required
- Any known valkuilen for that specific integration

Use this detection list as a starting point. Extend it freely based on what you find in the input.

**Triggers**
- Webhook: external systems pushing data to n8n. Always ask if a direct HTTP response is required within seconds. If yes, use Respond to Webhook as the first action node and handle the rest asynchronously.
- Schedule Trigger: time-based execution. Always confirm timezone explicitly.
- Email Trigger (IMAP): incoming email as trigger. Flag risk of duplicate processing.
- Form Trigger: n8n native form.

**Logic and routing**
- IF: two paths based on condition
- Switch: multiple paths based on value
- Merge: combining two streams (confirm mode: Append, Merge by Key, or Wait)
- Wait: pausing execution (use sparingly, flag if used as workaround for poor architecture)
- Filter: removing items based on condition
- Split Out: splitting array into individual items. Always pair with Aggregate at the end.
- Aggregate: combining items back into array

**Data transformation**
- Set: creating, renaming, or assigning fields
- Edit Fields: bulk field manipulation
- Code: JavaScript for complex logic (flag when a Set node would suffice)
- Information Extractor: structured data from unstructured text
- Text Classifier: routing based on text categories

**Communication**
- Send Email (SMTP): outgoing email
- Gmail / Outlook: OAuth-based email. Flag token expiry risk.
- Slack: messages, channels, notifications
- Microsoft Teams: messages and notifications
- WhatsApp (via community node or API): messaging
- Telegram: bot messages

**CRM and sales**
- HubSpot: contacts, deals, pipelines
- Salesforce: records and automation
- Pipedrive: deals and contacts

**Storage and files**
- Google Drive: file operations
- Dropbox: file operations
- SharePoint / OneDrive: Microsoft ecosystem
- AWS S3: object storage

**Databases**
- MySQL / PostgreSQL: direct database operations
- Airtable: structured data
- Notion: pages and databases

**Payments**
- Stripe: payments, subscriptions, webhooks
- Mollie: Dutch payment provider

**E-commerce**
- Shopify: orders, customers, products
- WooCommerce: orders and webhooks

**Calendar and scheduling**
- Google Calendar: events and availability
- Outlook Calendar: Microsoft ecosystem

**Forms**
- Typeform: form submissions via webhook
- JotForm: form submissions
- Gravity Forms: WordPress forms

**AI services**
- OpenAI: GPT models, embeddings
- Anthropic: Claude models
- Mistral: open-weight models
- AI Agent node: complex reasoning with tools and memory. Flag when simpler nodes suffice.
- Basic LLM Chain: simple text processing without tools or memory
- Text Classifier: categorization and routing

**Workflow management**
- Execute Workflow: calling sub-workflows. Always pass data explicitly and capture response.
- Error Trigger: catching and handling errors. Required in every production workflow.
- Stop and Error: intentional workflow termination with clear message
- Respond to Webhook: sending immediate HTTP response before async processing continues

**HTTP and APIs**
- HTTP Request: any external API. Always configure timeout. Always handle non-200 responses. Always check for pagination.

If a service is mentioned that is not on this list, research what n8n integration exists for it. If no built-in node exists, check if a community node is available. If neither exists, flag this clearly and suggest the HTTP Request node as fallback, or ask the user if they have API access.

### Step 3: Ask clarifying questions

Never proceed with gaps. Ask specific questions until every item below is answered.

**Mandatory questions (stop rule applies to these four):**

1. What triggers this workflow?
2. What is the exact data structure at the trigger point? (What fields arrive, in what format, from which system)
3. What is the desired end result?
4. What happens when something goes wrong? (Retry, alert, stop silently, compensating action)

**Stop rule:** If the user cannot answer any of the four mandatory questions, do not proceed. Explain clearly what is missing and why it is needed. Wait.

**Additional questions if not answered by the input:**

5. Are there conditions or decision points in the process?
6. Which external systems need to be connected?
7. Are credentials available for all required systems?
8. What is the volume expectation? (How many times per hour or day)
9. Are there timing requirements? (Must something happen within X seconds)
10. Does a webhook trigger require an immediate HTTP response? (If yes: within how many seconds)
11. Does the workflow process binary data or files? (PDFs, images, Excel, etc.)
12. What n8n version is running? (Self-hosted: check Settings > About. Cloud: check your plan page)
13. Are there personal data or sensitive data flowing through this workflow? (GDPR implications)
14. Is there a test environment separate from production?
15. Are there multiple source systems in different timezones?
16. Is this a new workflow or an improvement of an existing one?

### Step 4: Flag structural concerns before planning

Before writing the plan, check for these conditions and flag them explicitly if present:

**Subworkflow recommendation**
If the workflow has more than 15 nodes, or contains clearly distinct phases that could function independently, recommend splitting into a main workflow and one or more subworkflows. Explain why and propose the split points.

**Idempotency risk**
If the workflow could receive the same trigger twice, flag this. Propose a deduplication strategy: check for existing records before creating, use a unique identifier as a gate, or store processed IDs in a database.

**Volume and throttling**
If volume is high (more than 500 executions per hour), flag potential rate limiting from external APIs and recommend batching, throttling nodes, or queue patterns.

**GDPR flag**
If personal data flows through the workflow, flag this explicitly. Ask: how long should execution data be retained in n8n? Recommend setting a data retention policy in n8n settings. Note that n8n stores execution data including input and output by default.

**n8n execution limits**
If the workflow is expected to run longer than 60 seconds or process more than a few hundred items in a single execution, flag the default 120-second timeout and memory limits. Recommend splitting into smaller batches.

**Webhook security**
If the trigger is a Webhook, always ask what authentication method will be used. Never build a webhook without proposing at least one: header token, basic auth, or HMAC signature verification.

**Timezone mismatch**
If multiple systems are involved in different timezones, flag this. Add a timezone normalization step after the trigger.

**Binary data**
If files are involved, flag that binary data workflows require different node configurations and that large files can hit memory limits.

### Step 5: Present the workflow plan

Once all mandatory questions are answered and structural concerns are flagged, present a structured plan.

```
## Workflow Plan

### Goal
[One sentence]

### n8n version
[Version confirmed by user]

### Trigger
[Node, configuration summary, data structure, webhook authentication if applicable]

### Webhook response strategy
[Immediate response required: YES/NO. If YES: how it is handled asynchronously]

### Input validation
[Which fields are validated immediately after the trigger and what happens if they are missing]

### Steps
[Numbered list of every step with the node that handles it]

### Decision points
[Every IF or Switch with conditions and paths]

### External integrations
[Every system, node used, credentials required, known risks]

### Idempotency strategy
[How duplicate triggers are prevented or handled]

### Error handling and compensating actions
[Error Trigger, what notification is sent, what compensating actions run if partial execution occurred]

### Volume and throttling
[Expected volume, any rate limiting or batching measures]

### Timezone handling
[Relevant if multiple timezones are involved]

### Binary data handling
[Relevant if files are processed]

### GDPR and data retention
[Personal data present: YES/NO. Retention recommendation if YES]

### Subworkflow structure
[Single workflow or split into subworkflows. If split: which parts and why]

### Environment strategy
[Test vs production: credentials, webhook URLs, environment variables]

### Assumptions
[Every decision made without explicit user input, listed so the user can review and override]

### What this workflow does NOT cover
[Explicitly out of scope]
```

Then ask: "Does this plan match what you had in mind? Type PROCEED to build, or tell me what to adjust."

Do not build until the user types PROCEED.

---

## Phase 2: Build

Only start after the user has typed PROCEED.

### Output 1: n8n JSON

Generate a valid n8n workflow JSON that can be imported directly into n8n.

**JSON rules:**
- Use correct n8n node type identifiers (e.g. `n8n-nodes-base.webhook`, `n8n-nodes-base.httpRequest`)
- Every node must have a unique id, a name, a type, and position coordinates
- Connections must be explicitly defined between every node
- Credentials must be referenced by name with a placeholder (e.g. `"credentialName": "YOUR_SMTP_CREDENTIALS"`)
- No hardcoded secrets, API keys, passwords, or real URLs anywhere in the JSON

**Sticky note at workflow start must include:**
- Workflow name
- Version number (v1.0 for new, incremented for improvements)
- Date
- One-line description
- Webhook test URL and production URL (if webhook trigger)
- List of required credentials with placeholder names
- Changelog (for v2 and above: what changed from previous version)

**Node naming:**
- Descriptive names only. Not "HTTP Request" but "Get Order from Shopify".
- Names describe the action, not the node type.

**Input validation node:**
- Always add a validation step directly after the trigger
- Check that all expected fields exist and are not null or empty
- If validation fails: use Stop and Error with a clear message describing which field is missing

**Webhook authentication:**
- If trigger is a Webhook: always add header authentication or HMAC verification
- Document the expected header name and value in the sticky note

**Webhook response:**
- If immediate response is required: add Respond to Webhook as the first action after validation
- Continue the rest of the workflow after the response node

**Idempotency:**
- If deduplication is needed: add a database check or Set node with a unique key before any write operations
- Document the deduplication key in the sticky note

**Pagination:**
- If an HTTP Request or API node could return paginated results: implement a pagination loop
- Use the Split Out and Aggregate pattern to process all pages before continuing

**Timezone normalization:**
- If multiple timezones are involved: add a Code or Set node after the trigger to normalize all timestamps to UTC

**Binary data:**
- If files are processed: use the correct binary data node configurations
- Flag in the sticky note that large files may hit memory limits

**Error handling:**
- Always connect an Error Trigger node
- The error path must: capture the error message, send a notification (email or Slack), and document any compensating actions needed
- If partial execution can cause data inconsistency: add compensating action nodes on the error path

**Subworkflows:**
- If the plan calls for subworkflows: generate a separate JSON for each subworkflow
- Each subworkflow gets its own sticky note and version number
- The main workflow passes data explicitly to each subworkflow and captures the response

**Environment variables:**
- Use n8n environment variables for any value that differs between test and production
- Document all environment variables in the sticky note with: variable name, purpose, example value

**Community nodes:**
- If a community node is required: add a prominent comment in the sticky note with the npm package name and installation instructions

**Version and changelog in sticky note:**
```
Version: v1.0
Date: [date]
Author: n8n-workflow-builder skill

Changelog:
- v1.0: Initial version
```

After generating the JSON, add this note:
```
IMPORTANT: Before importing:
1. Search the JSON for "YOUR_" and replace all placeholders with your actual credential names
2. Search for "ENV_" and set the corresponding environment variables in your n8n instance
3. If community nodes are required, install them first via Settings > Community Nodes
4. Test in your test environment before activating in production
```

### Output 2: Mermaid diagram

Generate a Mermaid flowchart that visualizes the workflow.

Rules:
- Use `flowchart LR` (left to right)
- Every node in the workflow gets a box
- Decision points use diamond shapes
- Error paths are shown in red where Mermaid supports it
- Label every arrow with what data or condition triggers it
- If subworkflows exist: generate a separate diagram per subworkflow plus an overview diagram
- If the workflow is complex: split into sub-diagrams per major section with a legend

### Output 3: Markdown documentation

```
# [Workflow Name] v[version]

## What this workflow does
[2-3 sentences, plain language, no jargon]

## Trigger
[How and when the workflow starts, including authentication method for webhooks]

## Prerequisites
[Every credential needed, every external service to configure, every environment variable to set, every community node to install]

## n8n version
[Confirmed version]

## Input data structure
[Expected fields at trigger point with types and example values]

## Steps
[Numbered walkthrough of every step in plain language]

## Decision points
[Every condition with what happens on each path]

## Error handling
[What happens when something goes wrong, including compensating actions]

## Idempotency
[How duplicate triggers are handled]

## GDPR and data retention
[Personal data present: YES/NO. Retention recommendation. n8n execution data note.]

## Known limitations
[What this workflow does not handle, including n8n execution time and memory limits]

## Environment differences
[What differs between test and production: credentials, webhook URLs, environment variables]

## How to test
[Step-by-step testing instructions including test data examples for all scenarios including edge cases]

## Test data examples
[Sample input for happy path, error path, and edge cases]

## Maintenance notes
[Token expiry, rate limits, volume monitoring, n8n version upgrade considerations]

## Assumptions
[Every decision made without explicit user input]

## Changelog
[Version history]
```

---

## Quality checks before delivering

Before presenting any output, verify every item on this list:

**JSON**
- Valid JSON with no syntax errors and all brackets closed
- Every node has a unique id, name, type, and position
- No orphaned nodes (every node connects forward or to an error path)
- Trigger is correctly configured
- Input validation node is present directly after the trigger
- Error Trigger is connected and leads to a notification
- All credential placeholders start with YOUR_
- All environment variable placeholders start with ENV_
- No hardcoded secrets anywhere
- Sticky note is present with version, date, credentials, and changelog
- Webhook authentication is configured if trigger is a Webhook
- Pagination loop is present if API calls could return multiple pages
- Split Out nodes all have a corresponding Aggregate downstream
- Subworkflows pass data explicitly and capture response

**Mermaid**
- Diagram matches the JSON structure exactly
- All decision points are diamonds
- Error paths are visible

**Documentation**
- All sections are filled in
- Test data examples cover happy path, error path, and at least one edge case
- Assumptions section lists every undocumented decision
- Maintenance notes include token expiry and rate limit considerations

---

## What this skill does not do

- It does not configure credentials in n8n
- It does not guarantee the workflow works without testing
- It does not handle n8n version-specific breaking changes automatically
- It does not build workflows requiring community nodes without flagging installation
- It does not make assumptions about data structures it has not seen
- It does not provide legal advice on GDPR compliance
- It does not handle database schema migrations
- It does not manage n8n infrastructure or hosting
- It does not proceed without answers to the four mandatory questions

---

## Common mistakes this skill actively prevents

The most frequent n8n errors. The skill checks for all of these during the build phase.

**Triggers and input**
- Webhook without authentication
- Webhook without an immediate response when the calling system expects one
- Schedule Trigger without an explicit timezone
- No input validation after the trigger
- Missing null checks on expected fields

**Logic and data**
- IF node with wrong operator
- Merge node in wrong mode
- Split Out without a corresponding Aggregate downstream
- Timestamps from different timezones without normalization
- Hardcoded values that should be environment variables
- No pagination for API calls that can return multiple pages

**Execution**
- No idempotency for workflows that can be triggered more than once with the same data
- No compensating actions after partial execution on the error path
- No Error Trigger in the workflow
- Sub-workflows called without passing data or capturing the response
- Code node used where a Set node would suffice
- AI Agent node used for simple tasks where Basic LLM Chain is the better choice

**Technical limits**
- Workflows that can run longer than 120 seconds without batching
- Large binary files without memory considerations
- OAuth tokens that expire without a fallback
- HTTP Request without timeout configuration
- HTTP Request without handling of non-200 responses

**Maintenance and compliance**
- No version number in the workflow
- No changelog in the sticky note
- Personal data flowing through the workflow without a data retention consideration
- No distinction between test and production credentials

---

## Found something missing?

This skill is built on real-world n8n experience combined with systematic analysis. If you encounter a pattern it did not handle well, open an issue at the GitHub repository. That is how it gets better.

---

## Installation note

Works in both Claude Code and Claude.ai.

Place this file at `.claude/skills/n8n-workflow-builder/SKILL.md` in your project folder for project-specific use.

Or place it at `~/.claude/skills/n8n-workflow-builder/SKILL.md` to use it across all projects.
