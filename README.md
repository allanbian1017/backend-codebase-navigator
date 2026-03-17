# 🧭 Backend Codebase Navigator Agent Skill

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

A custom agent skill designed to analyze, and document unfamiliar backend codebases. 

Stepping into a new backend repository can be overwhelming. This skill acts as a Senior Staff Engineer pairing with you, stripping away boilerplate and noise to extract the core architectural context, data flow, and the "why" behind historical design decisions.

## 🎯 The Problem It Solves
Instead of mindlessly reading lines of code, this agent operates with a minimalist mindset to generate a **Minimalist Onboarding Survival Guide**. It systematically maps out dependencies (like `go.mod` or `package.json`), entry points (like `cmd/` or router setups), and critical domain logic, saving you hours of cognitive load.

## 📦 Installation

To use this skill, you need to have the Gemini CLI / Claude Code / Antigravity skills installed and configured.

1. Clone this repository or download the skill folder:
```bash
   git clone https://github.com/allanbian1017/backend-codebase-navigator.git
```

Move the folder into your Gemini CLI / Claude Code / Antigravity skills directory.

Ensure the structure looks like this:

```plaintext
backend-codebase-navigator/
└── SKILL.md
```


# 🗺️ What to Expect (The 4 Phases)
The agent is instructed to execute a strict 4-phase analysis and will output a clean Markdown document containing:

The 10,000-Foot View: A domain glossary and a Mermaid.js System Context Diagram mapping external integrations (PostgreSQL, Redis, Kafka, etc.).

The 1,000-Foot View: A flat directory map and a "Front Door" list identifying all primary API routes and event consumers.

Ground Level: A simplified Entity-Relationship (ER) model and a Sequence Diagram tracing the most critical "Happy Path" in the system.

Operational Reality: A copy-pasteable local setup runbook, "Trapdoors & Gotchas" for troubleshooting, and SCQA (Situation, Complication, Question, Answer) documentation for any complex historical design choices.

# 🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

# 📝 License
This project is licensed under the Apache License 2.0.