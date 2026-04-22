# Getting Started

This guide explains how to install and run skills depending on which Claude product you use.

There are three ways to use these skills:

- **Claude.ai or Claude Desktop** for the VA-light skill (no technical knowledge needed)
- **Claude Code** for the Website Builder and Code Modernizer skills (requires a terminal)
- **Claude.ai or Claude Code** for the n8n Workflow Builder (works in both)

---

## Option A: Claude.ai or Claude Desktop (VA-light)

This is the easiest route. No terminal. No technical setup.

**Step 1: Download the skill**

Go to the [VA-light skill file](va-light/SKILL.md) in this repository.

Click the download button in the top right (looks like an arrow pointing down) or copy the raw content and paste it into a text file. Save it as `SKILL.md`.

**Step 2: Fill in your details**

Open the file in any text editor (Notepad on Windows, TextEdit on Mac, or any other editor).

Replace everything between [ ] with your own information. For example:

```
- **Name:** [YOUR NAME]
```

becomes:

```
- **Name:** Sarah Johnson
```

Do this for every field. Save the file when done.

**Step 3: Install in Claude.ai**

1. Go to [claude.ai](https://claude.ai) and sign in
2. Click your profile icon and go to Settings
3. Navigate to Customize > Skills
4. Click the + button or Upload a skill
5. Select your filled-in SKILL.md file
6. Toggle the skill on

**Step 3 (alternative): Install in Claude Desktop**

1. Open the Claude Desktop application
2. Go to Settings
3. Navigate to Capabilities or Customize > Skills (depends on your plan)
4. Click the + button or Upload a skill
5. Select your filled-in SKILL.md file
6. Toggle the skill on

**Step 4: Start using it**

From now on, Claude picks up the skill automatically when relevant. Just type what you need in plain language:

- "Write an email to a client about a delayed delivery"
- "Summarize these meeting notes"
- "Help me write a LinkedIn post about this topic"

No extra instructions needed.

---

## Option B: Claude Code (Website Builder and Code Modernizer)

This option requires Claude Code and a terminal. It is intended for people who are comfortable with a command line.

**What you need:**

- A Claude Pro or Max subscription at [claude.ai](https://claude.ai)
- A computer with a terminal (Mac, Windows, or Linux)
- Node.js version 18 or higher

Not sure if you have Node.js? Open your terminal and type:

```
node --version
```

If you see a version number, you are good. If not, download Node.js at [nodejs.org](https://nodejs.org) and install it first.

**Step 1: Install Claude Code**

Open your terminal and run:

```
npm install -g @anthropic-ai/claude-code
```

Then log in:

```
claude login
```

This opens a browser window. Sign in with the same account you use on claude.ai.

**Step 2: Download the skill**

Go to the skill file in this repository (Website Builder or Code Modernizer) and download it.

**Step 3: Fill in your details**

Open the SKILL.md file in any text editor and replace all fields between [ ] with your own information. Save the file when done.

**Step 4: Set up the skill folder**

Create a new folder for your project. Inside that folder, create this structure:

```
my-project/
└── .claude/
    └── skills/
        └── [skill-name]/
            └── SKILL.md
```

Replace [skill-name] with `website-builder` or `code-modernizer`. Place your filled-in SKILL.md in that location.

**Step 5: Run Claude Code**

Open your terminal. Navigate to your project folder:

```
cd path/to/my-project
```

Start Claude Code:

```
claude
```

For the Website Builder, type:

```
Build my website based on the configuration in the skill.
```

For the Code Modernizer, type:

```
Analyze and modernize the code in this folder.
```

**What to expect:**

The Website Builder runs four agents across three phases. A complete website typically takes 15 to 30 minutes. Do not close the terminal while it is running.

The Code Modernizer runs a full analysis first and stops for your approval before touching any files. The original code is never modified.

---

## Option C: Claude.ai or Claude Code (n8n Workflow Builder)

The n8n Workflow Builder works in both Claude.ai and Claude Code. Choose the option that fits you best.

**What you need:**

- A Claude Pro or Max subscription
- An n8n instance (self-hosted or cloud at [n8n.io](https://n8n.io))

**Step 1: Download the skill**

Go to the [n8n Workflow Builder skill file](n8n-workflow-builder/SKILL.md) in this repository and download it. No fields to fill in for this skill. It works out of the box.

**Step 2a: Install in Claude.ai (easiest)**

1. Go to [claude.ai](https://claude.ai) and sign in
2. Go to Settings > Customize > Skills
3. Click the + button or Upload a skill
4. Select the SKILL.md file
5. Toggle the skill on

Then start a new conversation and describe what you want to automate. Claude will take it from there.

**Step 2b: Install in Claude Code (for terminal users)**

Place the file at `~/.claude/skills/n8n-workflow-builder/SKILL.md` to use it across all your projects.

Or place it at `.claude/skills/n8n-workflow-builder/SKILL.md` inside a specific project folder.

Then start Claude Code and describe what you want to automate.

**What to expect:**

The skill always analyzes first. It asks clarifying questions until it has everything it needs. Only after you type PROCEED does it build the workflow.

The output is three files: an importable n8n JSON, a Mermaid diagram, and Markdown documentation.

Before importing the JSON into n8n: search for `YOUR_` and replace all placeholders with your actual credential names from your n8n instance.

**Input options:**

- Describe what you want to automate in plain text
- Share a business plan or process document
- Upload a photo of a whiteboard or process diagram
- Paste an existing n8n JSON to improve or extend it

---

## Questions or issues?

Open an issue in this repository or reach out via [LinkedIn](https://www.linkedin.com/in/michaeldoomen).
