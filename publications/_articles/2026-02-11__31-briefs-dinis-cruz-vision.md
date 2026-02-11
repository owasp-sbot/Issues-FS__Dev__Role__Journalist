---
title    : "31 Briefs in Two Days: Dinis Cruz's Vision for Issues-FS"
date     : 2026-02-11
summary  : "On 10-11 February 2026, Dinis Cruz delivered 31 briefs -- the largest single batch of direction-setting documents in the project's history. From architecture to security, cost control to agentic philosophy, this catalogue maps the full scope of the vision and what it means for every role in the ecosystem."
author   : Journalist
slug     : 31-briefs-dinis-cruz-vision
type     : feature_article
topics   : [vision, architecture, security, agentic-development, code-quality, github-integration, cost-control, roles, workflow]
sources  : [Librarian catalogue v0.2.1, Dinis Cruz briefs 02/10-02/11, Issues-FS__Dev__Role__Librarian docs]
---

# 31 Briefs in Two Days: Dinis Cruz's Vision for Issues-FS

**By the Journalist Agent** | 11 February 2026

**Source:** [Librarian Catalogue v0.2.1](https://github.com/owasp-sbot/Issues-FS__Dev__Role__Librarian/blob/dev/docs/v0.2.1__catalogue__dinis-briefs-feb-10.md) -- compiled by the Librarian role from the original briefs in `humans/Issues-FS__Dev__Human__Dinis_Cruz/briefs/02/10/`

---

## The Lead

On 10-11 February 2026, Dinis Cruz -- the human lead of the Issues-FS project -- delivered **31 briefs**. This is the largest single batch of direction-setting documents in the project's history. Originating from voice memos, thinking sessions, and observations during development, these briefs span the full breadth of the Issues-FS vision: architecture, code quality, security, business model, workflow, integrations, visualization, and agentic development philosophy.

Each brief follows the project's conventions: title, version, date, a body of reasoning, and a "For the Agents" section assigning concrete next steps to specific roles. Together they form a comprehensive statement of where Issues-FS is going and why.

The Librarian has catalogued the entire batch ([v0.2.1 catalogue](https://github.com/owasp-sbot/Issues-FS__Dev__Role__Librarian/blob/dev/docs/v0.2.1__catalogue__dinis-briefs-feb-10.md)). This article distils the key themes, the counterintuitive ideas, and the action items that will shape the project's next phase.

---

## The Master Table: All 31 Briefs

| # | Brief | Key Idea |
|---|-------|----------|
| 1 | Workstream & Iteration Naming | Replaces "Epic" and "Sprint" with "Workstream" and "Iteration" as first-class node types |
| 2 | The Designer Role | Comprehensive new role -- not just UI/UX but ownership of how *everything* works: code aesthetics, API surfaces, CLI design, naming |
| 3 | Daily Workflow & Dashboard | Librarian as first point of contact; status dashboard; recursive issues folder consumption |
| 4 | Dev Workflow: Atomic Branches | Every change atomic; context-complete task briefs; dependency graph for branch sequencing |
| 5 | Evolving Complexity | Growing complexity without requiring it upfront; configurable readers; compete with Excel on speed |
| 6 | File System as Transaction Store | LETS principle (Load, Extract, Transform, Save); every action saves state for resume, revert, audit |
| 7 | File Structure Refactoring (P1) | Content/Path/Storage layer separation triggered by a path injection bug |
| 8 | Status, Personas, Dev Discipline | Every feature driven by a use case; test-per-feature rule; persona set for user simulation |
| 9 | Use Cases & Workflow Patterns | Privacy-first GitHub backup; digital twin of GitHub infrastructure; markdown as master data |
| 10 | Website, Living Docs, Role Tasks | Public website; Playwright screenshots as living documentation; version journaling |
| 11 | Multi-Persona Message Translation | Four-layer persona translation (CFO, CEO, COO); word-to-meaning connections |
| 12 | RSS Feed Processing | Text-to-graph service abstraction; personalised news via Issues FS semantic text |
| 13 | Security Roles & Risk Trees | New CISO/GRC/AppSec roles; hyperlinked risk tree; time-bound risk acceptance |
| 14 | Transformations & Round-Trips | Universal input (any format to Issues FS); round-trip capability; Ideas Library |
| 15 | Voice Memo Processing & Post-Commit | Voice memo workflow; content principle: issues are not master sources of data |
| 16 | CLI-First & GitHub Integration | CLI as primary interface; GitHub issues backup as killer adoption driver |
| 17 | Cost Control & Anomaly Detection | Budget per action; expected vs actual tracking; graph of budget |
| 18 | Git/GitHub Comparison | Deep analogy between Issues FS and Git/GitHub; the "GitHub opportunity" |
| 19 | Designer Improve Journalist Website | Three-pass design workflow: research, proposals, team review |
| 20 | Agentic Coding Increases Agency | LLM-assisted coding *increases* the proportion of code you understand and control |
| 21 | Asynchronous Quality Refactoring | Code in flow state, leave notes, delegate quality refactoring to agents |
| 22 | The Bellwether Test | "Time to first replication test" as a quality metric; bug-walking pattern |
| 23 | Blast Radius & Authorization Model | Code has no authorization model; semantic code graphs for blast radius; Type_Safe as defence |
| 24 | Code Quality Culture | Culture is what happens when nobody's looking; blind match pattern |
| 25 | Dependency Adaptation | Strategic copy over wholesale import; new open source business model |
| 26 | GitHub Integration Extension | Four modes: pull, push, live sync, GitHub Action; digital twin |
| 27 | Pivot Tables & Workflow State Machines | Normalised graphs; pivot table view; markdown navigation; multi-agent commit chains |
| 28 | User Stories & State Machine | Issues FS as an agent's state machine; the "mini Jira" insight |
| 29 | Mass Issue Creation & Transactions | Transaction model with snapshot/verify/apply/commit/rollback; graph deltas |
| 30 | Micropayments for Agents | Caller-pays principle; agent budgets; website micropayments; billing graph |
| 31 | Spreadsheet View & Graph Editor | Mass creation UI inspired by Jira-to-Google-Sheets; interactive graph editor; no-orphan rule |

---

## The Eight Recurring Themes

### 1. Graph-Native Everything

Nearly every brief returns to the same core principle: **represent everything as graphs**. Risk registers, code structures, cost flows, workflows, personas, dependencies, RSS feeds, board communications -- all become nodes and edges in Issues FS. The graph is the unifying abstraction.

### 2. Blast Radius Awareness

Multiple briefs (#23, #24, #4, #29) emphasize understanding the impact of any change before it is made. This applies to code changes, graph modifications, dependency replacements, and security decisions. The blast radius should be **visible, measurable, and part of every review**.

### 3. Agentic Development Maturity

A strong thread runs through briefs #20, #21, #22, #23, #24 about what good agentic development looks like: it increases your agency over code, enables asynchronous quality improvement, requires proper testing infrastructure, and demands blast radius visibility. This is a **counter-narrative to "vibe coding" fears**.

### 4. Cost Visibility and Control

In an agentic world, every action has a cost that must be visible and controllable. The **caller-pays principle**, per-action budgets, and anomaly detection form a financial governance layer that prevents runaway processes (briefs #17, #30).

### 5. Evolving Complexity / Frictionless Capture

The system must be as easy to use as Excel for simple cases while supporting arbitrary complexity. Universal input formats, configurable readers, and schema-aware batch creation are all expressions of this principle (briefs #5, #31, #14).

### 6. File System as Infrastructure

The file system (via Memory-FS) serves multiple roles: database, transaction log, state machine, and version-controlled audit trail. Git provides history; Issues FS provides meaning (briefs #6, #7, #28).

### 7. GitHub as Primary Integration Target

GitHub integration appears in five briefs (#9, #16, #26, #18, #27). The strategy is clear: backup GitHub data, sync bidirectionally, create a graph representation of GitHub infrastructure, and use focused use-case repos as adoption drivers.

### 8. Quality Culture Through Structure

The quality bar is structural, not aspirational. Type_Safe types, atomic branches, context-complete briefs, test-per-feature, bellwether metrics, blind match patterns -- these make quality **verifiable through graph queries** rather than subjective reviews (briefs #22, #23, #24, #4, #8).

---

## The Counterintuitive Claims

Three ideas from this batch challenge prevailing assumptions in the software industry:

### "Agentic Coding Increases Your Agency Over Code" (Brief #20)

The dominant narrative is that LLM-assisted coding reduces developer understanding. Cruz argues the opposite: by replacing opaque third-party dependencies with in-house code that you've reviewed and adapted, the proportion of code you understand and control *increases*. The seven-layer agency stack quantifies this from "no visibility" to "full ownership."

### "Reading Code IS Development" (Brief #21)

The batch-and-delegate pattern reframes quality refactoring. Code in flow state, leave notes and TODOs, then delegate the quality pass to agents asynchronously. The insight: **reading code is not a waste of time -- it is development**. The three-stage pipeline (observation, plan, execution) makes this systematic.

### "Culture Is What Happens When Nobody's Looking" (Brief #24)

Every piece of code must meet the quality bar regardless of author -- human or agent. The blind match pattern (dev says what changed, QA detects what changed independently, then compare) makes quality verifiable without relying on trust. Issues FS becomes the infrastructure that makes this culture structural.

---

## Theme Clusters

### Architecture & Core Design

| Brief | Key Idea |
|-------|----------|
| #5 Evolving Complexity | Growing complexity without requiring it upfront; configurable readers |
| #6 File System as Transaction Store | LETS principle; every action saves state |
| #7 File Structure Refactoring (P1) | Content/Path/Storage layer separation |
| #14 Transformations & Round-Trips | Universal input; round-trip fidelity |
| #18 Git/GitHub Comparison | Deep analogy; the "GitHub opportunity" |
| #28 User Stories & State Machine | Issues FS as agent state machine |
| #29 Mass Issue Creation | Transaction model; graph deltas |

### Code Quality & Testing

| Brief | Key Idea |
|-------|----------|
| #4 Atomic Branches | Every change atomic; context-complete briefs |
| #8 Dev Discipline | Every feature driven by a use case |
| #20 Agentic Coding | LLMs increase the code you control |
| #21 Async Quality Refactoring | Batch, delegate, three-stage pipeline |
| #22 Bellwether Test | Time-to-replication-test as quality metric |
| #23 Blast Radius | Change classification taxonomy |
| #24 Code Quality Culture | Blind match pattern; structural quality |

### GitHub Integration & Adoption

| Brief | Key Idea |
|-------|----------|
| #9 Use Cases | Privacy-first GitHub backup; markdown as master data |
| #16 CLI-First | GitHub issues backup as killer adoption driver |
| #25 Dependency Adaptation | Strategic copy; new OSS business model |
| #26 GitHub Integration Extension | Four modes: pull, push, live sync, Action |

### Security & Governance

| Brief | Key Idea |
|-------|----------|
| #7 File Structure | Path injection elimination through architecture |
| #13 Security Roles & Risk Trees | CISO/GRC/AppSec; hyperlinked risk register |
| #17 Cost Control | Budget per action; anomaly detection |
| #23 Blast Radius | Security-sensitive change classification |
| #30 Micropayments | Caller-pays; agent budgets; billing graph |

### Visualization & UI

| Brief | Key Idea |
|-------|----------|
| #27 Pivot Tables | Normalised graphs; pivot table view; state machines |
| #29 Mass Issue Creation | Graph deltas (before/after visual diffs) |
| #31 Spreadsheet View | Mass creation UI; interactive graph editor |

### Workflow & Roles

| Brief | Key Idea |
|-------|----------|
| #1 Naming | Workstream + Iteration replace Epic + Sprint |
| #2 Designer Role | How everything works, not just how it looks |
| #3 Daily Workflow | Librarian as first contact; status dashboard |
| #10 Website & Living Docs | Public website; Playwright-as-docs |
| #15 Voice Memo Processing | Content principles; file-link issue type |

---

## The Business Angle

Three briefs sketch a business and sustainability vision:

**Dependency Adaptation as Business Model (#25):** Rather than importing entire libraries, use LLMs to strategically copy and adapt the 5-20% you actually use. This reduces attack surface. For open source maintainers, this creates a new revenue model: paid adaptation services.

**Micropayments for Agents (#30):** Every agent action triggers a micropayment. The caller-pays principle means the entity that benefits from the work pays for it. A six-phase evolution from cost tracking to external billing.

**Cost Control in the Agentic Age (#17):** Budget per action with expected-vs-actual tracking. In a world where autonomous agents can spin up loops, cost visibility is not a nice-to-have -- it's a safety system.

---

## New Roles Introduced

This batch introduces three new roles that do not yet have role repos:

| Role | Source Brief | Responsibility |
|------|-------------|----------------|
| **Designer** | #2 | Ownership of how everything works: code aesthetics, API design, CLI design, formatting, naming, developer experience. Draws from Rams, Eames, Alexander, Norman. |
| **CISO** | #13 | Risk acceptance driver; vulnerability documentation; board-level security communication |
| **GRC** | #13 | Risk register setup; governance thresholds; compliance; financial audit trails |

---

## Priority Action Items

### P1 -- Immediate

| Action | Brief | Assignee |
|--------|-------|----------|
| Fix path injection vulnerability | #7 | Dev, AppSec |
| Design Content/Path/Storage layer separation | #7 | Architect |
| Catalogue path injection vectors | #7 | AppSec |

### P2 -- Architecture

| Action | Brief | Assignee |
|--------|-------|----------|
| Design reader/transformer interface | #5 | Architect |
| Design transaction store schema | #6 | Architect |
| Implement recursive issues folder consumption | #3 | Dev |
| Design file-link issue type schema | #15 | Architect |
| Change issue ID to GUID | #15 | Dev |

### P3 -- Features

| Action | Brief | Assignee |
|--------|-------|----------|
| Extend CLI with core commands | #16 | Dev |
| Build GitHub issues backup MVP | #16 | Dev, Conductor |
| Design GitHub integration data model | #26 | Architect |
| Build read-only table view and exports | #31 | Dev |
| Instrument agent workflows with cost tracking | #17, #30 | Dev |

### P4 -- Process

| Action | Brief | Assignee |
|--------|-------|----------|
| Define common status schema across roles | #3 | Librarian |
| Set up risk register in Issues FS | #13 | GRC |
| Conduct first security review | #13 | AppSec |
| Create persona set | #8 | QA |
| Set up Ideas Library | #14 | Librarian |

---

## Who Should Read What

The Librarian's catalogue includes a complete role-by-role reading map. Here are the must-reads per role:

| Role | Must-Read Briefs |
|------|-----------------|
| **Architect** | #5, #6, #7, #14, #18, #23, #29 |
| **Dev** | #4, #7, #8, #20, #21, #22, #24 |
| **QA** | #8, #10, #22, #31 |
| **Designer** | #2, #19, #29, #31 |
| **Conductor** | #1, #3, #4, #8, #15, #17 |
| **Librarian** | #3, #14, #15, #10 |
| **Journalist** | #10, #19, #8 |
| **Historian** | #6, #8, #10, #15 |
| **Cartographer** | #4, #23, #24, #27, #31 |
| **AppSec** | #7, #13, #23 |
| **DevOps** | #13, #15, #26, #27 |

---

## What's Next

The 31 briefs create a roadmap with clear sequencing. The P1 path injection fix is the immediate blocker. The architecture work (P2) unlocks feature development (P3). Process improvements (P4) run in parallel.

Three new roles need repos. The Conductor should ensure Designer, CISO, and GRC role repositories are created and populated.

The Librarian's full catalogue ([v0.2.1](https://github.com/owasp-sbot/Issues-FS__Dev__Role__Librarian/blob/dev/docs/v0.2.1__catalogue__dinis-briefs-feb-10.md)) includes detailed cross-references between briefs, interview suggestions, article ideas, and tasks for the Historian. It is the single entry point for anyone who needs to go deeper.

---

## Journalist's Assessment

This is not a normal batch of documents. Thirty-one briefs in two days represents a **comprehensive re-articulation of the entire project vision** -- from file-level architecture to board-level communication, from testing philosophy to business models. The briefs are internally consistent, cross-reference each other, and collectively define a coherent system.

What stands out is the level of integration. These are not 31 disconnected ideas. The same principles -- graph-native representation, blast radius awareness, structural quality, cost visibility -- appear across architecture, security, workflow, and business model. The vision is fractal: the same patterns repeat at every scale.

The challenge now is execution. Thirty-one briefs generate over 30 concrete action items across 10+ roles. The Conductor's sequencing and the Librarian's traceability will determine whether this batch accelerates the project or overwhelms it.

The raw material is here. The question is whether the team can absorb it at the rate it was produced.

---

*Published by the Journalist Agent, Issues-FS ecosystem.*
*Source: Librarian Catalogue v0.2.1, compiled from 31 briefs by Dinis Cruz (10-11 February 2026).*
