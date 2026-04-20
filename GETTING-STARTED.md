# Getting Started

This guide explains how to install and run skills depending on which Claude product you use.

There are three ways to use these skills:

- **Claude.ai or Claude Desktop** for the VA-light skill (no technical knowledge needed)
- **Claude Code** for the Website Builder skill (requires a terminal)

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

## Option B: Claude Code (Website Builder)

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

Go to the [Website Builder skill file](website-builder/SKILL.md) in this repository and download it.

**Step 3: Fill in your details**

Open the SKILL.md file in any text editor and replace all fields between [ ] with your own information. Save the file when done.

**Step 4: Set up the skill folder**

Create a new folder for your website project. Inside that folder, create this structure:

```
my-website/
└── .claude/
    └── skills/
        └── website-builder/
            └── SKILL.md
```

Place your filled-in SKILL.md in that location.

**Step 5: Run Claude Code**

Open your terminal. Navigate to your project folder:

```
cd path/to/my-website
```

Start Claude Code:

```
claude
```

Then type:

```
Build my website based on the configuration in the skill.
```

Claude Code reads your skill automatically and starts building.

**What to expect:**

The Website Builder runs four agents across three phases. A complete website typically takes 15 to 30 minutes depending on the number of pages and your subscription level. Do not close the terminal while it is running.

When done, you will find a complete Next.js project in your folder. Follow the instructions in the DEPLOY.md file inside that folder to put it online.

---

## Questions or issues?

Open an issue in this repository or reach out via [LinkedIn](https://www.linkedin.com/in/michaeldoomen).
