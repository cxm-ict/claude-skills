# Techniques

The professional build techniques for Phase 2. Apply what the task calls for, not everything at once. Each technique comes with the why, so you know when it pays off.

## Contents

1. Role instruction
2. Context and goal up front
3. Examples (few-shot)
4. Structured output
5. Reason step by step
6. Build in success criteria
7. Negative examples and limits
8. Variables for reusability
9. Order and layout of the prompt

---

## 1. Role instruction

Give the AI a clear role with fitting expertise. "You are an experienced client communication copywriter" steers tone and word choice more strongly than a bare instruction. Make the role specific to the task, not general.

## 2. Context and goal up front

Put who, what, and for whom at the top, before the instruction comes. The AI reads the instruction as a whole, but context up front colors everything that follows. Make the goal concrete: not "write something good" but the result the user pictures.

## 3. Examples (few-shot)

One example of desired output steers more powerfully than three paragraphs of explanation, especially for style, tone, and format. Where possible, give an example of good and optionally of bad. For reusable prompts: put examples in the template so they work along every time.

## 4. Structured output

Ask for a fixed format if the output is processed further or compared:

- For people: headings, a fixed layout, a list.
- For further processing by software: a schema with XML-like tags or JSON. Then explicitly ask for that format only, without introductory text around it.

A fixed format makes output predictable and therefore reusable.

## 5. Reason step by step

For tasks that require thinking (analysis, a tricky trade-off, code): ask the AI to first reason step by step before it gives a conclusion. Asking straight for the final answer on a complex problem more often yields a guess. For simple tasks this is unnecessary and only makes the output longer.

## 6. Build in success criteria

Work the criteria a good output meets into the prompt, for example: "The text succeeds if it is understandable at B1 level and ends with a clear follow-up step." This gives the AI a measuring stick and gives you something in Phase 3 to set the test output against.

## 7. Negative examples and limits

State explicitly what is not allowed: no jargon, no list of features, no promises outside policy, no longer than a certain number of words. Limits often steer just as strongly as instructions.

## 8. Variables for reusability

This makes the difference between a prompt for now and an asset for a hundred times. Replace every piece that changes each time with a clearly marked placeholder in curly braces:

```
Write a {message_type} to {audience} about {topic}.
Length: {length}. Tone: {tone}.
```

Keep the names expressive and consistent. Put a small list of the variables at the bottom of the template, so the user knows what to fill in.

## 9. Order and layout of the prompt

An order that works reliably:

1. Role and expertise.
2. Context: who, what, for whom.
3. The task and the goal, with success criteria.
4. Constraints: length, tone, format, what is not allowed.
5. Example or examples.
6. Optionally: ask to reason first, then answer.

Keep the prompt tight. Every line that steers nothing weakens the lines that do.
