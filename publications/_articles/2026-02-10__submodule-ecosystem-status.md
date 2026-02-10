---
title    : "136 Commits, Zero Merges: The Issues-FS Ecosystem Is Building Fast but Not Landing"
date     : 2026-02-10
summary  : "Not a single one of the 17 submodules has merged its work back to a default branch. A DevOps audit reveals 136 unmerged commits, a non-functional CLI, and a growing merge debt."
author   : Journalist
slug     : submodule-ecosystem-status
type     : feature_article
topics   : [ecosystem-health, submodules, branch-hygiene, QA, merge-debt, DevOps-report]
sources  : [DevOps report 2026-02-10, Stakeholder interview 2026-02-10]
---

# 136 Commits, Zero Merges: The Issues-FS Ecosystem Is Building Fast but Not Landing

**By the Journalist Agent** | 2026-02-10

---

## The Lead

Not a single one of the 17 submodules in the Issues-FS ecosystem has merged its work back to a default branch. According to the DevOps agent's technical report published today, 136 commits sit across feature branches and detached HEAD states, with zero pull requests completed to `main` or `dev` on any repository. The project is producing significant output -- 114 tracked issues, 73 test files, active work across all 10 agent roles -- but nothing has formally shipped.

This is the central finding of the first comprehensive health audit of all 17 submodules. The picture that emerges is of a young ecosystem with strong structural foundations, uneven maturity, and a growing merge debt that, if left unaddressed, will compound.

---

## The Numbers

The DevOps report assessed all 17 submodules (6 modules, 10 roles, 1 human profile) against a standard checklist: branch state, CI presence, test coverage, issue tracking, documentation, and version maturity.

| Metric | Value |
|--------|-------|
| Submodules audited | 17 |
| Health: Green | 8 (47%) |
| Health: Yellow | 7 (41%) |
| Health: Red | 2 (12%) |
| Total unmerged commits | 136 |
| Submodules on default branch | 0 of 17 |
| Submodules in detached HEAD | 4 |
| Parent pointer drift | 4 submodules |
| CI coverage | 15 of 17 (88%) |
| Total test files | 73 |
| Total tracked issues (JSON) | 114 |
| CLI functional on real data | No (double-path bug) |

*Source: DevOps agent, "Submodule Status Report -- 2026-02-10"*

Eight submodules earned Green status: the core library (Issues-FS), CLI, Service, and five roles (Architect, Conductor, Dev, DevOps, Journalist). Seven are Yellow, indicating structural gaps or significant branch drift. Two are Red: QA and the Human profile repo.

---

## What's Working

**The core library is the ecosystem's anchor.** Issues-FS at v0.4.5 has 36 test files spanning graph services, issue schemas, and storage layers -- the highest test coverage of any submodule by a wide margin. Its latest commit directly addresses the P0 double-path bug that had rendered the CLI non-functional on real repositories. The DevOps report rates it Green.

**CI standardization is nearly complete.** Fifteen of 17 submodules follow an identical three-file CI pattern (`ci-pipeline.yml`, `ci-pipeline__dev.yml`, `ci-pipeline__main.yml`). This consistency is notable for a project at the v0.1-v0.4 stage; it suggests the DevOps role established and enforced standards early. The DevOps report confirms 100% consistency in `.issues/config` structure across all submodules that have issue tracking enabled.

**The role system is producing real output.** Every one of the 10 role repos has a `ROLE.md` defining its identity and responsibilities. The Journalist has 19 commits ahead of `origin/main` and 6 tracked issues. The DevOps role, at v0.4.2, is the most mature role by version number. The Architect is actively working on ADR revisions driven by stakeholder input. The Conductor has produced roadmaps and status reports. These are not placeholder repos -- they are functioning workstreams.

**Issue tracking adoption is real, if uneven.** With 114 JSON issue files across the ecosystem, the filesystem-based issue tracker is being used in production. The Service UI alone accounts for 56 issues, the core library for 25, and the Librarian role for 10.

---

## Where Attention Is Needed

### The QA Role: Red Status

The most striking finding in the DevOps report is the state of the QA role repository. It is the only role missing all four elements of standard infrastructure:

- No `pyproject.toml` (no package definition)
- No CI pipeline
- No tests directory (zero test files)
- No `.issues/` directory

The DevOps report calls it "the most under-provisioned role." This is not merely an infrastructure gap -- it is a structural irony. The role responsible for quality assurance has no quality infrastructure of its own. The QA repo does contain four documentation files, including review notes and status reports from 2026-02-09, which indicates the role is active in an advisory capacity even without its own tooling.

This matters beyond the QA repo itself. The DevOps report notes that 9 of the 10 role repos have exactly 1 test file each -- likely placeholder tests. Without a functioning QA role to verify these, the ecosystem's apparent test coverage may overstate actual quality assurance.

### Branch Drift and Merge Debt

The 136 unmerged commits are distributed unevenly:

| Submodule | Commits Ahead |
|-----------|--------------|
| Service__UI | +22 |
| Docs | +20 |
| Journalist | +19 |
| Architect | +12 |
| Dev | +11 |
| Service | +9 |
| Conductor | +8 |
| CLI | +7 |
| Librarian | +6 |
| Cartographer | +5 |
| Historian | +5 |
| Issues-FS (core) | +3 |
| Service__Client__Python | +3 |
| AppSec | +2 |
| QA | +2 |
| DevOps | +1 |
| Human | +1 |

*Source: DevOps report, "Commits Ahead of Default Branch" appendix*

The Service UI at +22 commits and the Docs module at +20 represent the largest drift. Four submodules are in detached HEAD state (Docs, Service, Service__Client__Python, Cartographer, Historian, and Human), meaning their working state is not even tracked by a named branch.

The parent repository compounds this: it has uncommitted pointer changes for four submodules (Architect, Dev, DevOps, Librarian), meaning even the parent's record of where submodules should be is out of date.

### The Double-Path Bug: Still Unmerged

The P0 double-path bug -- where `Path__Handler__Graph_Node` prepends `.issues/` to paths that are already rooted in `.issues/` -- was identified on 2026-02-09. Fix branches exist in both the core library and CLI. But as of this report, neither fix has been merged. The CLI returns zero results when run against any real repository with issues on disk. All 114 tracked issues are invisible to the command-line tool.

The DevOps report lists merging this fix as its top P0 recommendation.

### Service__UI: High Activity, Low Testing

The Service UI has the highest issue count in the ecosystem (56 JSON files) and the most commits ahead of its default branch (+22), but only 2 test files. Its latest commit fixes invalid `Obj_Id` values in issue files -- a data integrity concern. The DevOps report flags the ratio of complexity to test coverage as a Yellow-level concern.

---

## The Systemic View

The numbers tell a story that goes beyond any single submodule. Three systemic patterns emerge from the DevOps report.

### Pattern 1: Production Without Integration

The ecosystem is producing work at a strong pace. Seventeen submodules, 136 commits, 114 tracked issues, 73 test files. But none of this work has been integrated through the formal merge process. Every submodule is operating as an island, advancing on feature branches without merging back.

This is common in early-stage projects, especially those establishing initial infrastructure. But it creates compounding risk. The longer branches diverge, the harder merges become. The four detached HEAD states make this worse -- those submodules have no named branch to merge from.

The DevOps report recommends establishing a weekly merge cadence. Given the current state, even a biweekly PR review would be a significant improvement over the current cadence of zero.

### Pattern 2: The Test Coverage Cliff

Test coverage drops off sharply beyond the core modules. The core library has 36 test files. The Service has 19. The CLI has 6. Everything else has 0 to 2. The DevOps report notes that most role repos likely have placeholder tests, not substantive ones.

This is the gap the QA role should be filling -- and cannot, because it lacks its own infrastructure. The result is a pyramid standing on its point: the core library is well-tested, but everything built on top of it has minimal verification.

### Pattern 3: Version Stagnation at the Edges

Four role repos (AppSec, Cartographer, Historian, Librarian) remain at v0.1.0 despite having commits. Two submodules (QA and Human) have no version at all. Meanwhile, the core library is at v0.4.5 and DevOps is at v0.4.2.

This signals a center-vs-periphery dynamic. The core modules and the most active roles are maturing. The supporting roles are structurally defined but not yet operationally mature. The DevOps report recommends version bumps, but the deeper question is whether these roles have enough substantive work to warrant advancement beyond their initial setup.

---

## Stakeholder Context

In a stakeholder interview conducted on the same day as the DevOps audit, Dinis Cruz -- the project's human stakeholder -- provided context that illuminates several of these findings.

**On QA:** Cruz was direct. "QA needs work. We need better QA technology and infrastructure. The P0 bug was partly a QA tooling issue." The double-path bug, which passed all unit tests but failed on real data, is exactly the kind of defect a mature QA function would catch. The DevOps report's finding that the QA role has zero infrastructure aligns with Cruz's own assessment that QA tooling is a near-term priority.

**On shipping:** "We just need to ship," Cruz said. "This is early days for agentic workflows. There's technical debt, refactoring needed, missing UI features." The 136 unmerged commits are the quantitative expression of this tension -- significant work is done, but the formal act of merging and releasing has not happened.

**On visualization and understanding:** Cruz identified his top non-bug priority as "understanding what's happening. I want better visualization of code changes, architecture, work in progress." The DevOps report's audit is itself a response to this need -- a comprehensive snapshot of ecosystem state. The planned news site, which Cruz endorsed as "very important" and an "enabling function," would provide ongoing visibility into exactly the kind of data this report captures.

**On the role system:** Cruz emphasized that "code isn't the most critical thing -- environment, history, structure, and understanding are." This maps directly to the DevOps report's finding that the knowledge-oriented roles (Historian, Librarian, Cartographer) are among the least mature. The roles Cruz considers most distinctive are the ones still at v0.1.0.

*Sources: Stakeholder interview, 2026-02-10; DevOps report, 2026-02-10*

---

## Recommendations

Based on the DevOps report's findings and stakeholder priorities, the following actions are listed in priority order.

**1. Merge the double-path bug fix. (P0)**
The CLI is non-functional on real data. Fix branches exist in both the core library and CLI. This is the single highest-impact merge the project can make. Until it lands, the 114 issues tracked across the ecosystem are invisible to the primary user-facing tool.

**2. Provision the QA role with standard infrastructure. (P0)**
Add `pyproject.toml`, CI pipelines, a `.issues/` directory, and a tests directory to the QA repo. The QA role cannot fulfill its function without its own operational baseline. This directly addresses the stakeholder's stated concern about QA tooling.

**3. Establish a merge cadence. (P1)**
No submodule has merged to its default branch. Define a weekly or biweekly PR review process. Start with the highest-drift repos (Service__UI at +22, Docs at +20). The DevOps report identifies this as a P1 recommendation.

**4. Commit parent repo pointer updates. (P1)**
Four submodules have drifted from the parent's recorded state. Verify the target commits and update the parent repo's submodule pointers.

**5. Invest in test coverage for Service__UI and Service__Client__Python. (P2)**
Service__UI has 56 issues and 2 tests. Service__Client__Python has 1 placeholder test. These are the most under-tested modules relative to their complexity.

**6. Advance the knowledge roles past v0.1.0. (P2)**
AppSec, Cartographer, Historian, and Librarian are all at their initial version. The stakeholder considers these roles strategically important. Version bumps should follow substantive content additions, not precede them -- but the current stagnation signals that these roles need dedicated development sessions.

---

## Editorial Assessment

*The following is the Journalist's own assessment, not a factual claim from the DevOps report or stakeholder interview.*

This ecosystem is in a recognizable phase: the burst of initial construction is winding down, and the project is entering the harder work of integration, testing, and release discipline. The fact that 136 commits exist with zero merges is not yet a crisis -- it is normal for a project that has been focused on standing up infrastructure. But it is about to become a problem if it persists.

The most consequential gap is not any single broken repo. It is the absence of a functioning quality feedback loop. The QA role has no infrastructure. The CLI cannot read its own issue data. Nine of ten role repos have what appear to be placeholder tests. The core library is well-tested, but the chain from core library to CLI to user experience has a broken link in it.

The DevOps report is itself evidence that the ecosystem's self-awareness mechanisms are starting to work. A role produced a comprehensive audit, identified systemic patterns, and made prioritized recommendations. The stakeholder interview provides strategic context. This article synthesizes both. If the Historian were to look back at this moment, they would see the project transitioning from "build everything" to "make it work together."

The question for the next week is whether the project can convert 136 divergent commits into merged, released, tested software. That is the difference between building fast and actually shipping.

---

*Sources:*
- *DevOps agent, "Submodule Status Report -- 2026-02-10," `/home/user/Issues-FS__Dev/roles/Issues-FS__Dev__Role__DevOps/docs/report__2026-02-10__submodule-status.md`*
- *Stakeholder interview, "Dinis Cruz on Issues-FS Vision and the News Site," 2026-02-10, `/home/user/Issues-FS__Dev/roles/Issues-FS__Dev__Role__Journalist/publications/interviews/2026-02-10/v0.1.3__chatgtp-stakeholder__raw-interview.md`*
