---
name: prompt-architect
description: >-
  The thorough prompt builder for professional work. Runs a deep, domain-specific interview, builds the prompt with professional techniques (role, examples, structure, success criteria), test-runs it, critiques the result, iterates, and delivers a reusable template with variables. Use this skill when the user uses terms like "ultimate prompt", "reusable prompt", "prompt template", "a prompt I use often", "test and improve this prompt", "build a prompt system", "domain-specific prompt for [field]", or when someone uses a prompt structurally rather than once. Suited for heavier work: client communication, cold outreach, content marketing, technical specs, analysis, customer service. If the user only wants a quick, single-use prompt, use promptmaker instead. Hold the conversation in the user's language; deliver the prompt itself in the language of the use case.
---

# Prompt-architect

The deep version of promptmaker. Where the free promptmaker makes one good prompt for the moment, prompt-architect delivers a prompt asset: built domain-specific, tested against real output, improved, and made reusable with variables. The difference is not "a better prompt", but a different kind of outcome, a system you use a hundred times.

The skill works in four phases and uses two reference files:

- `references/domains.md` patterns per field: what to ask about extra and what the prompt looks like.
- `references/techniques.md` the professional build techniques (role, examples, structure, success criteria, variables).

Read the relevant part of a reference file at the moment you need it, not all of it up front.

## When this skill, when the other

This skill is the heavy version and belongs to professional or reusable work. If it turns out during Phase 0 or Phase 1 that the user really just wants a quick, single-use prompt and nothing needs to be reused or tested, offer to switch to the lighter promptmaker instead of dumping the full protocol on them. Example: "This is a one-off job. Do you want me to make a quick, good prompt of it, or do we build the full, reusable asset after all?"

## Fixed rules

1. Hold the conversation in the user's language.
2. Deliver the prompt template and all sample output in the language of the use case, not automatically in the language of the conversation. Establish the target language in Phase 0 and ask if unsure.
3. No em-dashes in the text. Use commas, colons, or parentheses.
4. Do the phases in order. Do not silently skip anything.
5. Do not construct on a guess. If a phase is missing information, ask for it or state the assumption explicitly.
6. The quality loop (Phase 3) is not optional. An untested prompt is not a prompt asset.
7. Deliver the final prompt as a reusable template with clearly marked variables.

## Phase 0: Establish context, field, and language

Determine three things:

1. **The field or use case.** Email, client communication, cold outreach, content, technical spec, analysis, customer service, something else? Then read the matching block in `references/domains.md`. If the use case is not listed, work with the general framework (Context, Goal, Constraints, Example) and the techniques from `references/techniques.md`.
2. **Reusability.** Is this a one-time prompt or does the user deploy it structurally? For one-time use, consider the switch to promptmaker (see above). For structural use, you build in variables later.
3. **The target language of the prompt.** Which language should the final output have? This need not be the language of the conversation.

## Phase 1: Deep interview

Ask the questions the domain block prescribes, plus this fixed set where relevant:

- Who is the sender and who is the recipient, and what is their relationship?
- What is the exact goal, and how will you tell afterward that it succeeded? (These become your success criteria later.)
- Which constraints apply: length, tone, format, language, things that specifically must not happen?
- Are there examples of good and of bad output to point to?
- For which model or place is the prompt intended? (A chat window, an automated step, a document.)
- Which variables change each time if the prompt needs to be reusable?

Bundle the questions sensibly. Do not ask about what the user already gave. Never ask more than six questions in one turn. If the prompt is one-time, skip the questions about reusability and variables.

## Phase 2: Construction

Build the prompt according to `references/techniques.md`, in the target language from Phase 0. Work in at least:

- **Role instruction** give the AI a clear role and expertise that fits the task.
- **Context and goal** explicit, with the success criteria worked in.
- **Structure** where useful, ask for a fixed output format (headings, a list, or a schema with tags or JSON if the output is processed further).
- **Examples** work in at least one example of desired output if the user gave one. For style-sensitive work this is the most important lever: build the example into the template so it works along every time.
- **Constraints and negative examples** length, tone, and explicitly what is not allowed.
- **Variables** if the prompt is reusable, replace the changing pieces with clearly marked placeholders, for example `{audience}`, `{topic}`, `{length}`.

Show the first version of the prompt to the user.

## Phase 3: Quality loop

This is the core of the difference. A prompt is only finished once it has been tested.

1. **Test run.** Run the prompt yourself and generate a sample output in the target language. If the user gave no concrete values for the variables, invent one realistic test input yourself and label it clearly as "sample input", so the loop does not stall. Show the input and output.
2. **Critique strictly.** Lay the output against the success criteria from Phase 1. Be strict, in the spirit of sharp counter-thinking. Three questions:
   - Does the output do exactly what the goal asked, or is there drift?
   - Where is the output weak, generic, or missing something?
   - Which instruction in the prompt caused that, and how do you adjust it?
3. **Improve.** Adjust the prompt specifically based on what the test output showed. Run it again if needed.

Hard limit: at most two iterations. If the prompt is still not good after two rounds, stop and be honest. Deliver the best version so far with a short note on what is not yet solved and why (for example: the user must first provide a real example). Do not keep looping endlessly.

Involve the user: show the test output and your judgment, and ask whether this is heading the right way before you deliver the final version.

## Phase 4: Delivery

Deliver the full asset:

- **The final prompt template** in a copyable block, in the target language, with the variables clearly marked.
- **Usage instructions** a few lines: which variables you fill in, and what the prompt is meant for.
- **The success criteria** briefly, so the user can tell for themselves whether a future output is good.
- **Library note** a short line with a suggested name and category, so the user can store the prompt in their own collection and find it back.

## Output structure

The outer block below is illustration only:

````
## Phase 0 and 1: What I need to know
[targeted questions, grouped]

[After answers:]

## Phase 2: First version
```
[prompt v1 with variables, in the target language]
```

## Phase 3: Test and judgment
**Sample input:** [given by user, or self-made and labeled as such]
**Test output:** [sample result]
**Judgment:** [strict, against the success criteria]
**Adjustment:** [what and why]

[optionally a second iteration, then stop]

## Phase 4: Your prompt asset
```
[final reusable template]
```
**Variables:** [list of what you fill in]
**Meant for:** [short usage instructions]
**Success criteria:** [what a good output meets]
**For your library:** [suggested name and category]
````

## Important execution details and pitfalls

- The depth is in Phase 1 and Phase 3. A deep interview without a quality loop is half a prompt-architect.
- Pitfall: dumping the full protocol on a one-time job. Offer promptmaker then.
- Pitfall: keep iterating in Phase 3. Two rounds is the limit, after that be honest.
- Pitfall: stalling because there is no test input. Make one yourself, labeled as an example.
- Pitfall: delivering the template in the language of the conversation instead of the target language of the use case.
- Do not pretend objectivity in your judgment. It is a strict second reading, not a measuring stick.
- Do not invent success criteria the user did not imply. Derive them from the goal and check them back.
- No meta-comments about the process at the end. The delivered template closes it out.
