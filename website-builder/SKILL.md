---
name: website-builder
description: Multi-agent website builder using Claude Code. Use this skill whenever the user wants to build a complete, professional website from scratch. Activate when the user mentions building a website, landing page, business site, portfolio, or any multi-page web project. Also activate when the user provides a business plan and wants a website built from it. This skill coordinates four specialized agents — structure, content, design, and technical SEO — working in sequence to deliver a polished, deployable website.
---

# Website Builder — Multi-Agent

A Claude Code skill that builds a complete, professional website using four specialized agents.

**Stack:** Next.js + Tailwind CSS
**Output:** A fully working, visually polished, secure, and deployable website

---

## Requirements

This skill requires:
- Claude Code (does not work in Claude.ai)
- A Pro or Max subscription (building a full website is token-intensive)
- Basic comfort with a terminal

---

## Configuration

Fill in before running. The more detail you provide, the better the result.

**About you:**
- **Name:** [YOUR NAME OR COMPANY NAME]
- **Tagline:** [ONE SENTENCE THAT DESCRIBES WHAT YOU DO]
- **Website goal:** [e.g. showcase services, sell products, build credibility, generate leads]
- **Target audience:** [WHO visits this website — be specific]
- **Language:** [DUTCH / ENGLISH / GERMAN]
- **Tone:** [FORMAL / FRIENDLY / BOLD / MINIMAL / PREMIUM]

**Design:**
- **Primary color:** [HEX CODE — e.g. #1E3A5F, or describe: deep navy, warm orange, forest green]
- **Secondary color:** [HEX CODE or description — or write GENERATE to let the agent choose a matching color]
- **Font style:** [CLASSIC / MODERN / BOLD / ELEGANT — or write GENERATE]
- **Visual style:** [CLEAN / RICH / DARK / LIGHT / EDITORIAL]

**Content:**
- **Pages needed:** [e.g. Home, About, Services, Portfolio, Contact]
- **Content source:** [GENERATE AUTOMATICALLY / I WILL PROVIDE MY OWN TEXTS / EXTRACT FROM BUSINESS PLAN]
- **Business plan:** [ATTACH FILE or write NONE]
- **Existing taglines or key messages:** [PASTE HERE or write NONE]

**Technical:**
- **Images:** [UNSPLASH AUTOMATIC / I WILL PROVIDE MY OWN / NONE FOR NOW]
- **Contact form:** [YES / NO]
- **Google Analytics:** [YES / NO]
- **Newsletter signup:** [YES / NO]
- **Other integrations:** [e.g. Calendly, WhatsApp button, social links — or NONE]

---

## How it works

Four agents run in sequence. Each owns one domain. Each delivers clean output to the next.

---

## Agent 1 — Architect

**Role:** Reads the configuration, sets up the project, and builds the full page structure.

Instructions:
- Read the full configuration before doing anything
- If a business plan is attached: extract the core message, services, target audience, and tone before starting
- Initialize a Next.js project with Tailwind CSS and App Router
- Create a clean folder structure: `/app`, `/components`, `/lib`, `/public/images`, `/styles`
- Build empty page files for each page in the configuration
- Set up a shared layout with header, footer, and navigation
- Configure `tailwind.config.js` with a complete design system:
  - Use the primary and secondary colors from the configuration
  - Set up a font pairing that matches the requested font style (use Google Fonts via next/font)
  - Define a spacing scale, border radius style, and shadow system consistent with the visual style
- Set up a `constants/content.ts` file where all text content will be stored — never hardcode text inside components
- Output: complete project scaffold with design system, ready for content

---

## Agent 2 — Copywriter

**Role:** Writes or refines all website content based on the configuration and any provided materials.

Instructions:
- If business plan is provided: extract all relevant information — services, mission, differentiators, target audience, tone — and use it as the foundation for all copy
- If own texts are provided: sharpen, structure, and adapt them to each page format
- If generating automatically: write all content based on the configuration details
- Write in the specified language and tone
- Never use filler phrases like "Welcome to our website" or "We are passionate about"
- Every page gets: headline, subheadline, body copy, and a clear call to action
- Home: hero with a bold value proposition, 3 concrete benefits, social proof section, closing CTA
- About: origin story or mission, what makes this different, a human element
- Services: each service gets a name, one-line description, 3 outcomes (not features), and a CTA
- Portfolio (if requested): project titles, one-line descriptions, and results
- Contact: short human intro, form labels, and a response time expectation
- Store all copy in `constants/content.ts` using the structure set up by Agent 1
- Output: complete content file, organized by page and section

---

## Agent 3 — Designer

**Role:** Builds all visual components and ensures a polished, consistent result across every page.

Instructions:
- Work strictly within the design system set up by Agent 1
- Build reusable Tailwind components: Hero, Section, Card, Button (primary + secondary), NavBar, Footer, Badge, Testimonial
- Apply visual hierarchy consistently: H1 only once per page, clear H2/H3 structure, readable line heights (1.6 minimum for body text)
- Add purposeful micro-interactions: fade-in on scroll using Intersection Observer, smooth hover states on all interactive elements, subtle button press effect
- Images:
  - If Unsplash automatic: use the Unsplash Source API with relevant search terms per section (e.g. `https://source.unsplash.com/1200x800/?[keyword]`). Choose keywords that match the industry and visual style
  - If own images provided: use `/public/images/` with next/image optimization
  - If none: use solid color blocks or abstract SVG patterns that match the brand colors — never leave empty boxes
- Ensure full responsiveness: 375px mobile, 768px tablet, 1280px desktop
- Check all text contrast ratios meet WCAG AA standards
- Every page must feel intentional — not like a template
- Output: complete styled website, visually consistent across all pages

---

## Agent 4 — Technical & SEO

**Role:** Makes the website fast, secure, findable, and ready to deploy.

Instructions:

**SEO:**
- Write unique meta title and description for every page (title max 60 chars, description max 155 chars)
- Add Open Graph and Twitter Card tags to all pages
- Add Schema.org structured data: Organization on homepage, WebSite, ContactPage if applicable, Service for each service
- Generate `sitemap.xml` and `robots.txt`
- Add `canonical` tags to all pages

**Performance:**
- Configure `next/image` for all images with correct `width`, `height`, and `priority` on above-the-fold images
- Add `loading="lazy"` to below-the-fold images
- Minimize unused CSS by purging Tailwind correctly
- Set up `next.config.js` with image domains and compression

**Security:**
- Add security headers in `next.config.js`:
  - `Content-Security-Policy`
  - `X-Frame-Options: DENY`
  - `X-Content-Type-Options: nosniff`
  - `Referrer-Policy: strict-origin-when-cross-origin`
  - `Permissions-Policy`
- Ensure no API keys or secrets are exposed in client-side code
- Add `.env.example` with all required environment variables documented

**Integrations (based on configuration):**
- Contact form: build with React Hook Form, add field validation, success and error states, and connect to a free form service (Formspree or Web3Forms) — document setup in DEPLOY.md
- Google Analytics: add GA4 with `next/script`, respect cookie consent, document the measurement ID setup in DEPLOY.md
- Newsletter signup: add email capture with confirmation state, connect to Mailchimp or Brevo free tier — document in DEPLOY.md

**Deployment:**
- Write a clear `DEPLOY.md` with:
  - Step-by-step Vercel deployment (recommended — free tier works for most sites)
  - How to connect a custom domain
  - How to set up environment variables
  - How to submit the sitemap to Google Search Console
  - What to do after launch: Google Analytics verification, form testing, mobile check

**Output:** Technically complete, secure, and fully deployable website with clear deployment instructions

---

## Handoff order

1. Agent 1 reads configuration (and business plan if provided), sets up scaffold and design system
2. Agent 2 writes all content in parallel with Agent 1 when possible, stores in `constants/content.ts`
3. Agent 3 builds all visual components and applies content from Agent 2
4. Agent 4 runs last — after all pages and styles are finalized

---

## Quality check before delivering

Before marking the project complete, verify:
- All pages render without console errors
- Navigation works correctly on all pages and on mobile
- No [ ] placeholders remain anywhere in the codebase
- All images load correctly
- Mobile layout looks correct at 375px
- All form fields validate correctly (if contact form is included)
- `DEPLOY.md` is present, complete, and accurate
- `.env.example` documents all required variables
- Running `npm run build` completes without errors

---

## Installation note

This skill requires Claude Code. It does not work in Claude.ai.

Replace all fields between [ ] in the configuration section before running.

A Pro or Max subscription is recommended — building a complete website uses significant context.
