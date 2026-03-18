---
name: backend-codebase-navigator
description: Sequentially reverse-engineers, analyzes, and documents unfamiliar backend codebases to extract architectural context, dependencies, and operational workflows.
version: 1.0.0
pattern: Pipeline
---

# 🎯 Purpose
To systematically guide the agent in analyzing an unfamiliar backend repository, extracting architectural context, data flows, and operational procedures, and synthesizing this information into a concise, highly structured documentation artifact.

# 🚪 Gating & Trigger Conditions
- **When to invoke:** The user requests an architectural overview, documentation generation, or onboarding guide for an unfamiliar or undocumented backend repository.
- **When NOT to invoke:** The user asks for targeted bug fixes, single-function explanations, or code refactoring (this pipeline is too heavy for narrow tasks). 

# 📥 Input Specifications
- **Codebase Context:** The root directory path or loaded workspace containing the target repository.
- **Target Feature (Optional):** A specific business flow or feature to trace for the "Happy Path".

# ⚙️ Execution Instructions (Workflow)
1. **Phase 1: 10,000-Foot View (Context & Architecture)**
   - Scan `README.md`, `Dockerfile`, CI/CD configurations, and any existing architectural docs.
   - *Fallback:* If `README.md` is missing, scan top-level directory names and environment variable files (e.g., `.env.example`) to infer infrastructure.
   - Extract a 3-5 term **Domain Glossary**.
   - Generate a **System Context Diagram** (Mermaid.js) mapping external integrations.
2. **Phase 2: 1,000-Foot View (Dependencies & Entry Points)**
   - Parse package manager files (e.g., `go.mod`, `package.json`, `requirements.txt`, `pom.xml`) to identify frameworks and database drivers.
   - *Fallback:* If package files are missing, scan main entry files for `import` or `require` statements.
   - Map a 2-level deep **Directory Map**.
   - Compile a **"Front Door" List** (Markdown table) of primary entry points, routers, or event listeners.
3. **Phase 3: Ground Level (Data Flow & Domain Logic)**
   - Locate primary domain entities (structs, classes, interfaces).
   - Trace the single most critical feature path (or user-provided target) from transport to persistence.
   - Generate an **ER Model** (Mermaid.js) for the top 3-5 data structures.
   - Generate a **Sequence Diagram** (Mermaid.js) for the traced "Happy Path".
4. **Phase 4: Operational Reality & Historical Context**
   - Identify local execution commands (e.g., `Makefile`, `package.json` scripts, migration folders).
   - Synthesize a copy-pasteable **Local Setup Runbook**.
   - Locate complex/non-standard logic and document it using the **SCQA Framework** (Situation, Complication, Question, Answer).
   - *Fallback:* If no obvious setup scripts exist, provide generic run instructions based on the identified language/framework.
   - Create a **Trapdoors & Gotchas** section logging inferred potential startup errors.

# 📤 Output Specifications
- A single, well-structured Markdown document.
- Minimalist text explanations emphasizing bullet points and tables.
- Valid Mermaid.js code blocks for all required diagrams.

# 📁 References & Directory Structure
