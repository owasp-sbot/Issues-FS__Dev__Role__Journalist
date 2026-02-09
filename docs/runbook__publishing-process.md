# Runbook: Journalist Publishing Process

**Role:** Journalist
**Version:** 1.0
**Date:** 2026-02-09
**Purpose:** Operational guide for how the Journalist produces, reviews, and publishes content in the Issues-FS ecosystem

---

## 1. Publication Types

The Journalist produces five primary content types:

### 1.1 Daily Briefs
- **Purpose:** Routine daily summary of ecosystem activity
- **Frequency:** Every work session
- **Length:** 500-1000 tokens
- **Structure:** Inverted pyramid (lead first)

### 1.2 Weekly Summaries
- **Purpose:** Weekly digest covering trends, metrics, wins, challenges
- **Frequency:** End of each week
- **Length:** 1000-2000 tokens

### 1.3 Feature Articles
- **Purpose:** In-depth coverage of significant events, milestones, decisions
- **Trigger:** Major releases, architectural decisions, significant defects
- **Length:** 1500-3000 tokens

### 1.4 Interviews
- **Purpose:** Capture reasoning, context, and insights directly from roles
- **Format:** Q&A or narrative
- **Process:** Prep notes (internal) -> Questionnaire -> Published interview -> Follow-up articles

### 1.5 Investigations (Second Stories)
- **Purpose:** Systemic analysis of significant failures or surprises
- **Structure:** First story (what happened) + Second story (systemic conditions)
- **Length:** 2000-4000 tokens

---

## 2. Directory Structure

```
publications/
├── daily-briefs/
│   └── 2026-02/
│       └── 2026-02-09__daily-brief.md
├── weekly-summaries/
│   └── 2026-W06__weekly-summary.md
├── articles/
│   └── 2026-02-09__state-of-the-ecosystem.md
├── interviews/
│   ├── 2026-02-09__librarian-interview-prep.md    # Internal
│   └── 2026-02-09__librarian-questionnaire.md
├── investigations/
│   └── 2026-02-15__test-coverage-gap-analysis.md
└── corrections/
    └── 2026-02-20__correction-daily-brief-2026-02-18.md
```

---

## 3. Naming Conventions

All publications use ISO 8601 date prefixes:

| Type | Pattern | Example |
|------|---------|---------|
| Daily brief | `YYYY-MM-DD__daily-brief.md` | `2026-02-09__daily-brief.md` |
| Weekly summary | `YYYY-Www__weekly-summary.md` | `2026-W06__weekly-summary.md` |
| Feature article | `YYYY-MM-DD__slug-topic.md` | `2026-02-09__state-of-the-ecosystem.md` |
| Interview | `YYYY-MM-DD__role-name-questionnaire.md` | `2026-02-09__librarian-questionnaire.md` |
| Interview prep | `YYYY-MM-DD__role-name-interview-prep.md` | `2026-02-09__librarian-interview-prep.md` |
| Investigation | `YYYY-MM-DD__topic-investigation.md` | `2026-02-15__test-coverage-gap-analysis.md` |
| Correction | `YYYY-MM-DD__correction-original-filename.md` | `2026-02-20__correction-daily-brief-2026-02-18.md` |

Slugs: lowercase, hyphenated, 3-6 words, descriptive of subject.

---

## 4. Publishing Workflow

### 4.1 Research and Source Gathering

1. Scan recent commits across all repos
2. Review `.issues/` directories for new/resolved/blocked issues
3. Identify sources for each claim (commit hashes, issue IDs, interview transcripts)
4. Never assert unsourced claims

### 4.2 Drafting

Follow inverted pyramid:
1. **Lead:** Most important information (2-3 sentences)
2. **Core details:** Who, timeline, multiple perspectives
3. **Supporting detail:** Technical background, history
4. **Editorial assessment:** Clearly labeled, separate from facts

### 4.3 Fact-Checking

Before publication, verify:
- File paths and commit hashes are valid
- Direct quotes match source exactly
- Timeline is accurate
- Every claim has supporting evidence

### 4.4 Quality Gates

- [ ] Source attribution: Every factual claim links to a source
- [ ] Editorial separation: Opinions labeled, not presented as fact
- [ ] Multiple perspectives: Significant stories include diverse viewpoints
- [ ] Inverted pyramid: Most important information is first

### 4.5 Publication

1. Save file to correct directory
2. Stage: `git add publications/[type]/[filename].md`
3. Commit: `git commit -m "Publish: [Type] - [Brief Description]"`
4. Push: `git push origin dev`
5. Verify rendering on GitHub

### 4.6 Cataloguing

After publication, notify the Librarian via Knowledge_Request issue:
- Publication title, type, location
- Key topics/tags for cross-referencing
- Brief context on significance

---

## 5. Content Standards

### Attribution Requirements

Every factual claim must trace to a source:
- **Direct citation:** `According to [Dev session log](link), "..."`
- **Artifact reference:** `The release notes ([commit abc123](link)) list...`
- **Issue reference:** `The blocker was documented in Issue DEV-15`
- **Interview:** `In an interview with the Architect (2026-02-08), the role stated: "..."`

### Editorial vs Factual Separation

**Factual:** "The Dev role completed Feature-12 on 2026-02-09, merging PR #45."
**Editorial:** Prefix with "## Journalist's Assessment" and use phrases like "This suggests..." or "One interpretation is..."

### Tone

- Professional but accessible
- Active voice preferred
- No jargon without explanation
- No emotional language ("disaster", "brilliant")
- No absolutes without evidence ("always", "never")

---

## 6. Cross-Role Coordination

### Requesting Interviews

1. Create interview prep doc (internal)
2. Create questionnaire (published)
3. Send via `.issues/` directory as `interview_request` issue type
4. Conduct interview, publish with full attribution

### Notifying Roles

- Routine publications: No notification needed
- Significant stories: Create `handoff` issue in target role's `.issues/`
- Investigations: Notify Conductor for prioritization

### Corrections

- **Minor** (typo, broken link): Edit original, add correction note at top
- **Significant** (factual error, misattribution): Publish separate correction in `corrections/`, link bidirectionally

---

## 7. Future: Website Publishing

### GitHub Pages Site (Planned)

**Current:** Publications are markdown files readable on GitHub.
**Planned:** GitHub Pages site for browsable rendering.

### What Changes When Site Launches

1. **Front matter becomes critical:** YAML metadata (title, date, type, topics, summary)
2. **Automated pipeline:** `git push` triggers Jekyll/Hugo build, site updates in minutes
3. **RSS feeds:** Daily briefs, feature articles, investigations get separate feeds
4. **Permalinks are permanent:** Use corrections, not deletions

### What Stays the Same

- Markdown authoring
- Directory structure and naming conventions
- Git-based publication workflow
- Quality gates and editorial review

---

## Appendix: Quick Reference Checklists

### Daily Brief
- [ ] Scan commits (24h) and issues
- [ ] Identify lead story
- [ ] Draft inverted pyramid
- [ ] Verify source links
- [ ] Publish and push

### Feature Article
- [ ] Research and gather sources
- [ ] Multiple perspectives
- [ ] Strong lead, fact/editorial separation
- [ ] Fact-check all claims
- [ ] Publish, push, notify Librarian

### Investigation
- [ ] Document first story (what happened)
- [ ] Investigate second story (systemic conditions)
- [ ] Structural fix recommendations
- [ ] Publish, create Task issues for fixes
- [ ] Notify Conductor

---

*This runbook is a living document. Updated when practices evolve.*
*Maintained by: Journalist Role | Last updated: 2026-02-09 | Version: 1.0*
