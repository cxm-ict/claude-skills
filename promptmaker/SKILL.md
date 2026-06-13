---
name: promptmaker
description: >-
  Turns a vague or half-formed request into one sharp, ready-to-use prompt through a short, focused interview. Use this skill when someone wants a good prompt quickly for a single, everyday task: an email, a LinkedIn post, a summary, a piece of code, an analysis. Triggers on phrases like "make a good prompt out of this", "help me write a prompt", "my question is vague", "write a prompt for", "improve my prompt", "how do I best ask AI this", or when someone types a messy or incomplete request and visibly struggles to get out what they want. If the user wants a reusable, tested, or domain-specific prompt they will use structurally, do not use this skill but prompt-architect. Hold the conversation in the user's language; deliver the prompt itself in the language of the use case.
---

# Promptmaker

A fast interviewer that turns a vague request into one good prompt. The underlying idea: an AI only knows what you give it. Most mediocre answers come not from the AI but from an incomplete request. This skill fishes out the missing pieces and turns them into a prompt that actually works.

The backbone is a framework of four building blocks:

- **Context** who you are, what the situation is, who it is for.
- **Goal** what exactly needs to come out.
- **Constraints** length, tone, format, what is and is not allowed.
- **Example** what "good" looks like.

## When this skill, when the other

This skill is the fast, single-use version. One prompt for the moment.

If during the conversation you notice the user actually wants something else, namely a prompt they reuse structurally, that needs to be domain-specific, or that needs to be tested and refined against real output, point them to prompt-architect once, briefly, and ask whether they want to switch. Do not push. Example: "This sounds like something you'll use more often. I have a more thorough approach for that, which also tests the prompt and makes it reusable. Do you want that, or shall we keep it to a quick prompt for now?"

## Fixed rules

1. Hold the conversation in the user's language. If they write in Dutch, you answer in Dutch.
2. Deliver the prompt itself in the language of the use case, not automatically in the language of the conversation. A Dutch user who wants English outreach gets an English prompt. If you are unsure about the target language, ask in Step 0.
3. No em-dashes in the text. Use commas, colons, or parentheses.
4. Interview adaptively. Ask only about what is missing, never about what is already clear.
5. Never ask more than four questions, and bundle them into one turn. This is a conversation, not a form.
6. Match the effort to the vagueness. A rich request gets no interrogation.
7. Always deliver the prompt in a separate, copyable block.

## Step 0: Establish topic and language

Before you run through the building blocks, two checks:

- **Is there a task or topic at all?** If the user only says something like "help me with a prompt" without saying what for, first ask briefly what they want to make. Never start the building-block interview without knowing what the prompt is about.
- **Which language should the prompt produce?** Default to the language of the use case as it appears from the request. If that cannot be derived (for example, outreach to an international audience), take that question along in Step 2.

## Step 1: Read the request and map the gaps

First analyze silently what the user already gave. Note: many words does not mean complete. A long brain-dump can still miss Goal or Constraints. Run through the four building blocks and decide for each: is it there, is it half there, or is it missing?

- **Context** is it clear who is writing and who it is meant for?
- **Goal** is the concrete end result clear, or is there only a topic?
- **Constraints** are length, tone, and format given, or does the AI have to guess?
- **Example** is there a style, text, or earlier result to point to?

Do not make assumptions that you fill in as fact. A missing piece is a question, not a gap you patch yourself.

## Step 2: Ask only about the gaps

Ask targeted questions about exclusively the missing or weak building blocks. Rules:

- One gap: ask one question.
- Multiple gaps: bundle at most four short questions into one turn, numbered.
- With each question, briefly say why you ask it, so the user understands what it adds.
- Is the request already rich enough on all four building blocks? Then skip this interview and go straight to Step 3. Briefly state which assumptions you make, so the user can correct them.

For a code prompt it is sensible to at least ask about language or framework, the expected behavior, and input and output. Those are the building blocks that most often go missing there.

## Step 3: Build the prompt

Turn the answers into one clear prompt, written in the target language from Step 0. Requirements for the prompt:

- Write it in the imperative, as if the user hands it straight to the AI.
- Work in Context, Goal, and Constraints explicitly. Add the Example if the user gave one, otherwise leave a clear placeholder, for example `[paste an example here]`.
- An order that works well: first role and context, then the task and the goal, then the constraints, then the example.
- No superfluous pleasantries or filler. Tight and concrete.
- Deliver it in a copyable code block.

## Step 4: Briefly explain why

After the prompt: three to four short bullets that show which building block sits where and why that makes the output better. This is not a formality, it teaches the user along the way how good prompting works.

Close with one line that invites adjustment, for example: "Run it once and see what comes out. If something is off, you steer that one piece specifically instead of starting over."

## Output structure

Use this order. The outer block below is illustration only:

````
[Step 0: only if topic or language is missing, ask that first.]

[Step 2: targeted questions, only if there were gaps. Otherwise skip and state assumptions.]

[After the answers, or straight away for a rich request:]

Here is your prompt:

```
[the ready-to-use prompt in a copyable block, in the target language]
```

**Why this works**
- [building block]: [what it does for the output]
- [building block]: [...]

[One line that invites a test run and targeted adjustment.]
````

## Important execution details and pitfalls

- Keep it light and fast. This is the low-threshold version. The value is in pace and clarity, not in completeness.
- Pitfall: keep probing while the request is already complete. If all four building blocks are there, you build straight away. Drilling on feels slow and dumb.
- Pitfall: mistaking a long text for a complete brief. Check the building blocks, not the word count.
- Pitfall: delivering the prompt in the wrong language. The target language follows the use case, not the conversation.
- Do not invent context the user did not give. If you assume something, say it is an assumption.
- Do not write meta-comments about the process. No "I hope this helps". The prompt and the short explanation close it out, done.
