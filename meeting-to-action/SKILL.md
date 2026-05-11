---
name: meeting-to-action
description: Use this skill whenever the user wants to turn raw meeting notes, a voice memo, handwritten notes (typed, photographed, or PDF), or a description of what was discussed into a structured meeting report with decisions, action points, and owners. Activate when the user pastes meeting notes, says "maak hier een verslag van", "zet dit om naar actiepunten", "meeting-to-action", "notulen maken", "wat zijn de acties", "verwerk deze vergadering", uploads a PDF or photo of meeting notes, or shares any unstructured text about a meeting or conversation. Also activate when the user says "ik had een gesprek over X" and wants a structured output. Works in Dutch and English.
---

# Meeting-to-action

A skill that turns any raw meeting input into a clean, structured report ready to send.

**Input:** Typed notes, voice memo transcripts, descriptions, PDFs from a Remarkable, or photos of handwritten notes from any source (tablet, phone, notebook, whiteboard).

**Output:** A structured meeting report with decisions, action points, owners and next steps. Delivered as PDF, Word document, or Markdown.

---

## Phase 1: Read the input

Identify what type of input was provided and process accordingly.

**Typed notes or transcript**
Read everything first. Strip filler words, repetition, and stream of consciousness. Extract structure.

**Description**
The user describes what happened in their own words. Extract the key points.

**PDF from a tablet**
Read the full content. PDFs from tablets sometimes contain a mix of handwriting recognition output and typed text. If recognition quality is poor, flag unclear sections and mark them with [?].

**Photo of handwritten notes (any source)**
First transcribe what you can read. Then explicitly list anything illegible or uncertain, marked with [?]. Ask the user to clarify those specific parts if they are critical for the action points or decisions. Do not guess at illegible words.

For handwritten input, add this note at the top of the report:
```
Note: this report is based on handwritten notes. Items marked [?] could not be read with certainty. Please verify before sending.
```

**Minimal input**
Only a topic or a few sentences. Ask the clarifying questions in Phase 2 before proceeding.

---

## Phase 2: Ask clarifying questions

Always ask these two questions first, regardless of how complete the input is:

1. Should the report be in Dutch or English?
2. In what format do you want the output: PDF, Word document (DOCX), or Markdown (MD)?

Then ask only what is still missing from the input:

**Mandatory if missing:**
3. Who attended the meeting? (names and roles if possible)
4. Who was not present but should receive this report? (distribution list for absentees)
5. What was the goal of the meeting?
6. What was decided? (if not clear from the notes)
7. Who is responsible for which action? (if not mentioned)

**Optional but useful:**
8. What is the deadline for the action points?
9. Is there a next meeting planned? If so: when, where, and with whom?
10. Were any documents, presentations, or references mentioned during the meeting?
11. Does this report contain confidential information? If yes, a confidentiality notice will be added.
12. Should this report be approved before sending? If yes: by whom?

If the input contains enough information to answer questions 3 through 7, skip those and only ask questions 1 and 2.

The report is always written for two audiences: people who attended the meeting and people who did not. The summary must be self-explanatory without prior context.

---

## Phase 3: Build the report

Adapt the level of detail to the complexity of the meeting. A 15-minute standup gets a shorter report than a 2-hour strategy session.

### Report structure

```
# Meeting report: [topic or project name]

[CONFIDENTIAL] ← only if the user confirmed confidential content

**Date:** [date if mentioned]
**Location / platform:** [physical location or video platform]
**Attendees:** [names and roles of people present]
**Not present / for information:** [names and roles of people receiving the report but not at the meeting]
**Goal:** [one sentence: what was this meeting supposed to achieve]
**Version:** v1.0

---

## Summary
[2-4 sentences. Written for both attendees and people who were not present. Self-explanatory without prior context. What was the occasion, what was discussed, what was the overall outcome. No bullet points. Plain prose.]

---

## Decisions
[List only confirmed decisions. If something was discussed but not decided, it goes under Open questions.]

- [Decision 1]
- [Decision 2]

If no decisions were made, write: "No formal decisions were made in this meeting."

---

## Action points

| Action | Owner | Deadline |
|--------|-------|----------|
| [What needs to be done, specific and concrete] | [Name or role] | [Date or "TBD"] |

If no owner was assigned, write "TBD" and add a note that ownership needs to be confirmed.

---

## Open questions
[Things that were raised but not resolved. Questions that need an answer before work can proceed.]

- [Question 1]
- [Question 2]

If there are no open questions, omit this section.

---

## Next meeting
[Date, time, location or platform, and purpose. If not yet scheduled, write "To be scheduled."]

---

## References
[Documents, presentations, or other materials mentioned during the meeting. Include a link or file name where possible.]

If no references were mentioned, omit this section.

---

## Approval
[If approval is required before sending: "This report is a draft and requires approval from [name] before distribution."]

Omit this section if no approval is required.

---

*Generated by meeting-to-action skill. Review before sending.*
*v1.0 | [date]*
```

---

## Rules for writing the report

**Action points must be concrete.**
Not "discuss further" but "schedule a follow-up meeting with the client by Friday." Not "look into options" but "research three alternatives for the payment provider and share findings in Slack by Wednesday."

**Decisions must be final.**
If something was discussed but not decided, it is an open question, not a decision.

**Owners must be specific.**
If a name was not mentioned, write "TBD" and flag it. Never assign an action to "the team" if one person should own it.

**Summary is prose, everything else is structured.**
No bullet points in the summary. Clear bullet points and a table for actions.

**Language follows the user's choice.**
The user picks the language in Phase 2. Do not switch language mid-report.

**Never invent information.**
If something is unclear, mark it with [?] and list it under assumptions. Do not fill gaps with guesses.

**Tone is direct and professional.**
Short sentences. No filler. No corporate speak. No phrases like "it was discussed that" or "there was a conversation about." State what happened directly.

**No em-dashes.**
Use a comma or a period instead.

---

## After the report

Add this section at the end of the chat (not in the report itself):

```
Assumptions made:
[List every piece of information that was not explicitly in the input but was assumed to complete the report. If no assumptions were made, omit this.]

To do before sending:
- Confirm owner for any TBD action points
- Fill in the date if missing
- Review action point deadlines
- Add any missing attendees
- Verify any items marked [?] (for handwritten input)
```

---

## Output format

Generate the report in the format the user selected in Phase 2:

**Markdown (MD):** Deliver as a clean .md file ready to download or paste.

**Word document (DOCX):** Generate a properly formatted .docx file with a title, clear headings, the action points as a real table, and professional but simple formatting.

**PDF:** Generate a clean, readable PDF with the same structure as the DOCX version.

In all cases: the file must be ready to forward without further editing, except for items explicitly flagged as TBD or [?].

---

## What this skill does not do

- It does not schedule meetings or send emails.
- It does not remember previous meetings unless you paste the notes.
- It does not make decisions for you. It only captures what was decided.
- It does not guarantee completeness if the input is incomplete. What goes in determines what comes out.

---

## Using with handwritten notes

This skill works with handwritten notes from any device or source: a Remarkable tablet, an iPad, an iPhone, a notebook, or a whiteboard photo.

**PDF export:**
Export your notes as PDF from your tablet app, upload to Claude, and type "meeting-to-action" or "maak hier een verslag van."

**Photo of handwritten notes:**
Take a photo with your phone, tablet, or camera. Upload the image. The skill will first transcribe what it can read, flag anything unclear, and then build the report.

For best results:
- Make sure the photo is well-lit and in focus
- Photograph straight on, not at an angle
- If you use abbreviations or personal symbols, mention what they mean
- Confirm the transcription before the report is generated if accuracy is critical

---

## Found something missing?

This skill is a first version. If you run it and it misses something important for your type of meetings, open an issue at github.com/cxm-ict/claude-skills.

---

## Installation

Works in both Claude.ai and Claude Desktop.

Go to Settings > Customize > Skills > click the + button > Upload this SKILL.md file.

From that point, Claude picks up the skill automatically whenever you paste meeting notes or ask for a structured report.

---

## License

CC BY-NC-SA 4.0, free to use and adapt for non-commercial purposes. Attribution required. Commercial use is not permitted without written permission.

Contact: michael@cxm-ict.com
