# Getting Started

This guide walks you through installing Claude Code and running your first skill.

---

## What you need

- A Claude Pro or Max subscription at [claude.ai](https://claude.ai)
- A computer with a terminal (Mac, Windows, or Linux)
- Node.js installed (version 18 or higher)

Not sure if you have Node.js? Open your terminal and type:

```
node --version
```

If you see a version number, you are good. If not, download Node.js at [nodejs.org](https://nodejs.org) and install it first.

---

## Step 1: Install Claude Code

Open your terminal and run:

```
npm install -g @anthropic-ai/claude-code
```

Then log in with your Anthropic account:

```
claude login
```

This opens a browser window. Sign in with the same account you use on claude.ai.

---

## Step 2: Download a skill

Go to the skill you want to use in this repository and click the file name to open it.

Then click the download button (top right, looks like an arrow pointing down) or copy the raw content.

Save the file as `SKILL.md` on your computer.

---

## Step 3: Set up the skill folder

Claude Code looks for skills in a specific location. Create the folder structure like this:

**For the VA-light skill:**

The VA-light skill is installed via Claude.ai, not Claude Code. Go to:

Settings > Profile > Skills > Upload file

Upload your filled-in `SKILL.md` and you are done.

**For the Website Builder skill:**

Create a new folder for your website project. Then inside that folder, create this structure:

```
my-website/
└── .claude/
    └── skills/
        └── website-builder/
            └── SKILL.md
```

Place your filled-in `SKILL.md` in that location.

---

## Step 4: Fill in your details

Open the `SKILL.md` file in any text editor (Notepad, TextEdit, or VS Code).

Replace everything between [ ] with your own information. For example:

```
- **Name:** [YOUR NAME]
```

becomes:

```
- **Name:** Michael Doomen
```

Do this for every field. Save the file when done.

---

## Step 5: Run Claude Code

Open your terminal. Navigate to your project folder:

```
cd path/to/my-website
```

Then start Claude Code:

```
claude
```

Type your request in plain language. For the Website Builder, something like:

```
Build my website based on the configuration in the skill.
```

Claude Code reads your skill automatically and gets to work.

---

## What to expect

For the Website Builder: Claude Code will run four agents in sequence. This takes time. A complete website typically takes 15 to 30 minutes depending on the number of pages and your subscription level.

Do not close the terminal while it is running.

When it is done, you will find a complete Next.js project in your folder. Follow the instructions in `DEPLOY.md` inside that folder to put it online.

---

## Questions or issues?

Open an issue in this repository or reach out via [LinkedIn](https://www.linkedin.com/in/michaeldoomen).
