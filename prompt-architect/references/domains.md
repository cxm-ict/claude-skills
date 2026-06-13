# Domains

Patterns per field. Per domain: what you ask about extra in Phase 1, and how the prompt is built in Phase 2. Read only the block that fits the user's use case.

## Contents

- Client communication (CCM)
- Cold outreach and sales
- Content marketing and social
- Technical spec and PRD
- Analysis and summary
- Customer service and replies

---

## Client communication (CCM)

Letters, emails, and messages an organization sends to customers. Often bound to tone of voice, legal correctness, and readability.

**Ask about extra:**
- Which type of message: informative, a rejection, a reminder, an apology, a change?
- Is there a fixed tone of voice or house style? Is there a sample letter?
- Which language level should the text have? (Often B1 for a broad audience.)
- Are there mandatory elements: a legal passage, an option to object, a reference number?
- Does it need to scale across many customers with varying data?

**Build approach:**
- Role: an experienced client communication copywriter who writes at the requested language level.
- Work in the mandatory elements as hard requirements.
- Ask for a fixed structure: cause, core, consequence or action, closing.
- Variables for everything that differs per customer: `{customer_name}`, `{reference}`, `{amount}`, `{date}`.
- Success criterion is often: correct, understandable at the requested level, and in the right tone.

---

## Cold outreach and sales

First approach to a prospect via email or message. The goal is a reply, not a sale in one go.

**Ask about extra:**
- Who is the prospect and what is their likely pain?
- What is the single desired follow-up action: a conversation, a click, a reply?
- How warm is the lead? Is there a trigger or shared context?
- What is the offer in one sentence, and what makes it credible?

**Build approach:**
- Role: someone who writes sharp, short outreach that does not read like a template.
- Hard constraints: short, one clear ask, no list of features.
- An example of a good and a bad version helps enormously; ask for one.
- Variables: `{prospect}`, `{trigger}`, `{pain_point}`, `{follow_up_action}`.
- Success criterion: would this prospect reply to it, or does it sound like the hundredth email they got?

---

## Content marketing and social

Posts, articles, newsletters. Often in a recognizable personal voice.

**Ask about extra:**
- Which platform and which format? (A LinkedIn post reads differently than a blog.)
- Is there an own voice or style? Ask for two to three examples of earlier work.
- What is the core message or the hook?
- What should the reader feel or do after reading?

**Build approach:**
- Capturing the voice through examples is the most important lever here. Without an example it becomes generic.
- Ask for a strong opening, because the first line decides whether someone reads on.
- Constraints: length, hashtags or not, emoji or not, tone.
- Variables: `{topic}`, `{hook}`, `{core_message}`, `{call_to_action}`.
- Success criterion: does it sound like the user themselves, and does the opening hold attention?

---

## Technical spec and PRD

A specification, a product requirements document, or a technical explanation.

**Ask about extra:**
- Who reads this: a developer, a client, a mixed audience?
- Which level of detail is needed, and which assumptions must not stay implicit?
- Is there a fixed template structure that must be followed?
- Must edge cases, risks, or acceptance criteria be stated explicitly?

**Build approach:**
- Role: an experienced engineer or product owner who writes clearly and completely.
- Enforce a fixed structure with headings: goal, scope, requirements, edge cases, acceptance criteria.
- Ask the AI to make assumptions explicit instead of silently filling them in.
- Variables: `{feature}`, `{audience}`, `{scope}`.
- Success criterion: can a developer build with this without having to ask back?

---

## Analysis and summary

Summarizing or analyzing a document, dataset, or text.

**Ask about extra:**
- What is the question behind the summary? A decision, an overview, a check?
- Which length and which format: bullets, an executive summary, a table?
- What may go and what must absolutely be kept?
- Should the output give an opinion or stay strictly neutral?

**Build approach:**
- Role: an analyst who separates main points from side issues for the requested purpose.
- Ask for a fixed structure that fits the decision that follows.
- Have the AI first restate the core question before it summarizes, so the focus is right.
- Variables: `{source_type}`, `{purpose_of_summary}`, `{length}`.
- Success criterion: can the reader make the decision the summary was meant for based on this?

---

## Customer service and replies

Answers to customer questions, complaints, or reviews.

**Ask about extra:**
- What is the tone of the incoming message: neutral, angry, disappointed?
- What may and may not be promised? Are there policy limits?
- Should a follow-up action or compensation be included?
- Does a house style apply for service replies?

**Build approach:**
- Role: an experienced service agent who responds calmly, acknowledging, and solution-oriented.
- Hard limit: never promise anything outside the given policy.
- Structure: acknowledge, explain, offer a solution or follow-up step, close warmly.
- Variables: `{customer_message}`, `{policy_room}`, `{follow_up_action}`.
- Success criterion: does the customer feel heard and is the next step clear?
