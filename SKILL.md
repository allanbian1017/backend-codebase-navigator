---

name: backend-codebase-navigator
description: Use this skill to reverse-engineer, analyze, and document unfamiliar backend codebases. It guides the agent to extract architectural context, dependencies, and operational workflows systematically.
---

# Backend Codebase Navigator & Documenter

This skill guides the agent to act as a Senior Staff Backend Engineer, exploring an unfamiliar repository with a minimalist mindset. The goal is to extract maximum architectural context and operational reality while ignoring boilerplate, focusing heavily on uncovering the "why" behind system design.

## Output Constraints
- Present the final artifact as a single, well-structured Markdown document.
- Keep explanations extremely concise. Use bullet points and tables where possible.
- Focus purely on the specific domain logic and structural decisions of the target repository.

## Workflow

Follow these four phases sequentially when analyzing the codebase:

### 1. The 10,000-Foot View (Context & Architecture)
- **Scan Core Files**: Review `README.md`, `Dockerfile`, CI/CD configurations, and high-level architectural documents.
- **Identify Infrastructure**: Pinpoint external dependencies (e.g., PostgreSQL, Redis, Kafka).
- **Deliverables**: 
  - Extract a concise **Domain Glossary** defining 3-5 core business terms used in the system.
  - Generate a text-based **System Context Diagram** using Mermaid.js showing the service and its external integrations.

### 2. The 1,000-Foot View (Dependencies & Entry Points)
- **Analyze Dependencies**: Read the package manager file (e.g., `go.mod` for GoLang projects, `package.json`, etc.) to determine the primary frameworks, transport protocols, and database drivers.
- **Map Structure**: Map the top-level directory structure (e.g., distinguishing between executable entry points and private business logic).
- **Deliverables**:
  - Create a flat **Directory Map** (maximum two levels deep).
  - Compile a **"Front Door" List** (a markdown table) identifying the primary application entry points, router initializations, or event consumer listening points.

### 3. Ground Level (Data Flow & Domain Logic)
- **Identify Core Entities**: Locate the domain entities (structs, classes, or interfaces) that represent the primary business value.
- **Trace the Happy Path**: Trace the single most critical feature path from the transport layer down to the persistence layer.
- **Deliverables**:
  - Sketch a simplified **Entity-Relationship (ER) Model** using Mermaid.js for the top 3-5 core data structures.
  - Generate a **Sequence Diagram** (Mermaid.js) mapping the critical "Happy Path" you traced.

### 4. Operational Reality & Historical Context
- **Scan Operational Scripts**: Look for test suites, database migration scripts, and local execution commands (e.g., `Makefile` targets).
- **Analyze Complexity**: Identify one area of complex or non-standard logic that might confuse a new engineer.
- **Deliverables**:
  - Write a copy-pasteable **Local Setup Runbook** (exact terminal commands to start the database, run migrations, and boot the server).
  - Document the complex logic using the **SCQA Framework** (Situation, Complication, Question, Answer) to clarify the historical context and architectural decisions.
  - Create a **Trapdoors & Gotchas** section logging potential startup errors and their 1-line solutions.