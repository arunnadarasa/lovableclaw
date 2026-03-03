# lovableclaw

**Lovable Skill for the OpenClaw Clinical Hackathon** — a Cursor Agent Skill that helps hackathon participants get from idea to a working clinical or healthcare app on [Lovable](https://lovable.dev) quickly and safely.

---

## About

This repository contains a **ClawHub-style skill** (a Cursor Agent Skill) aimed at participants of the **OpenClaw Clinical Hackathon**. The skill teaches an AI agent how to guide you when you're building clinical or healthcare applications with Lovable: patient intake forms, assessment tools, dashboards, and similar MVPs — with attention to auth, data modeling, and PHI-safe practices.

- **Lovable** is a full-stack AI development platform: you describe what you want in natural language and it generates and iterates on a live web app (React front end, Supabase-backed).
- **OpenClaw** is a self-hosted gateway that connects chat apps (WhatsApp, Telegram, Discord, iMessage, etc.) to AI coding agents.
- **ClawHub** ([clawhub.com](https://clawhub.com)) is where you discover and share skills that extend how agents behave.

Together, this skill bridges Lovable’s app-building workflow with the OpenClaw/clinical hackathon context so you can ship a small clinical MVP fast.

---

## What’s in this repo

| Path | Purpose |
|------|--------|
| `.cursor/skills/clawhub-lovable/SKILL.md` | The main skill file: instructions, quick start, clinical patterns, and examples for the agent. |

The skill is a **project skill**: it lives inside this repo. When you (or your team) open this project in **Cursor**, the agent can use it automatically when you’re working on Lovable projects or clinical apps.

---

## Who this is for

- **Hackathon participants** building a clinical or healthcare app with Lovable.
- **Developers** who want a quick, repeatable path from “clinical idea” to “deployed MVP” on Lovable.
- **Teams** who want consistent guidance on PHI-safe prompting, auth-first design, and scope (e.g. intake → list, or assessment → result).

---

## How to use the skill

### In Cursor (recommended)

1. **Clone this repo** (or use it as your project):
   ```bash
   git clone https://github.com/arunnadarasa/lovableclaw.git
   cd lovableclaw
   ```
2. **Open the project in Cursor.**  
   Cursor loads project skills from `.cursor/skills/`, so the agent will have access to the Lovable + clinical guidance.
3. **Ask in natural language**, for example:
   - “I’m doing the OpenClaw Clinical Hackathon and want to build a patient intake form in Lovable.”
   - “How do I make sure I don’t leak PHI when building with Lovable?”
   - “What’s the fastest way to get a clinical dashboard live?”

The agent will follow the skill’s quick start, clinical patterns, and Lovable best practices when answering.

### Skill triggers

The agent is instructed to use this skill when you:

- Mention the **OpenClaw Clinical Hackathon**, **Lovable**, or a **clinical project**.
- Say you want to build a **clinical/healthcare app** (intake forms, dashboards, assessments, vitals, etc.).
- Ask for **quick start** or **getting started** with Lovable for clinical use cases.

---

## Quick start (first clinical project in Lovable)

If you’re starting from zero, this is the path the skill recommends:

1. **Account and project**
   - Sign up at [lovable.dev](https://lovable.dev) and create a new project.
   - Name it clearly (e.g. “Patient Intake MVP”, “Clinical Dashboard”).

2. **Scope with Plan mode**
   - In Lovable, use **Plan mode** first. Describe your clinical goal (e.g. “Patient intake form with consent and basic demographics, then a simple list view”).
   - Get a high-level plan and break the app into **components** (e.g. intake form, list, detail view).

3. **Build by component**
   - Use **Agent mode** to implement one component at a time.
   - Prompt for **that component** (e.g. “Add a patient intake form with fields: name, DOB, consent checkbox, submit”) instead of “build the whole app”.
   - Add **authentication early** if the app will show any user-specific or sensitive data.

4. **Backend and data**
   - Use **Lovable Cloud** (Supabase) for database and auth so you don’t manage servers.
   - Prefer **structured fields** (demographics, assessments) in the database from the start; avoid free-text blobs for anything that might be PHI.

5. **Publish**
   - Use Lovable’s deploy/publish flow when the MVP is ready; add a custom domain later if needed.

---

## Clinical project patterns

The skill encodes these patterns so the agent can suggest them consistently:

- **Auth from day one**  
  If the app touches patient or user-specific data, add auth (e.g. Supabase Auth) at the start so you don’t retrofit it later.

- **PHI-safe prompts and logs**  
  Do **not** put real patient names, IDs, or clinical content in prompts or in logs. Use placeholders in prompts (e.g. “patient name field”, “DOB field”) and keep real data only in the database and in the running app.

- **Common clinical UIs**
  - **Intake**: Form with demographics, consent, and optional referral reason.
  - **Assessments**: Step-by-step or single-page forms with scores/results stored in the DB.
  - **Dashboards**: Read-only or summary views (e.g. list of patients, vitals summary) with filters and simple charts.

- **Keep scope MVP**  
  One clear workflow (e.g. “intake → list” or “assessment → result”) is enough for the hackathon; add features after the core works.

---

## Lovable best practices (summary)

- **Plan before prompt**: Use Plan mode to get a component-level plan, then implement in Agent mode.
- **Prompt by component**: One prompt per component or small feature; avoid “build entire app” in one go.
- **Use Knowledge**: Upload design system, brand, or API docs as a Knowledge file so prompts stay consistent.
- **Credits**: Lovable uses credits for generation; smaller, focused prompts use them more efficiently.

For full Lovable docs, see [docs.lovable.dev](https://docs.lovable.dev).

---

## OpenClaw and ClawHub

- **OpenClaw**: Self-hosted gateway for chat apps (WhatsApp, Telegram, Discord, iMessage, etc.) and AI agents. Useful if you want to expose a clinical workflow via chat (e.g. “start intake via Telegram”). See [docs.openclaw.ai](https://docs.openclaw.ai).
- **ClawHub**: [clawhub.com](https://clawhub.com) — skills discovery. Look here for more skills (e.g. health assistant, automation) that can complement a Lovable-built clinical UI.

---

## Repository structure

```
lovableclaw/
├── .cursor/
│   └── skills/
│       └── clawhub-lovable/
│           └── SKILL.md    # Agent skill: quick start, clinical patterns, examples
├── README.md               # This file
└── LICENSE                 # MIT
```

---

## Contributing

Improvements to the skill (e.g. clearer quick start, more clinical patterns, or better examples) are welcome. Open an issue or a pull request on the [GitHub repo](https://github.com/arunnadarasa/lovableclaw).

---

## License

MIT — see [LICENSE](LICENSE) in this repository.
