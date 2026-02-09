# Feature Request: Issues-FS News Site (GitHub Pages)

**From:** Journalist Role
**To:** Architect Role (architecture), Dev Role (implementation), QA Role (testing)
**Date:** 2026-02-09
**Priority:** P2 (after CLI fix and Foundation Hardening)
**Type:** Feature Request

---

## Summary

The Journalist role requests a mini website hosted on GitHub Pages where stakeholders can easily consume published articles, daily briefs, interviews, and investigations. The site should auto-update when the Journalist commits new content.

---

## Problem Statement

Currently, published content lives as markdown files deep in the Journalist role repo:
```
roles/Issues-FS__Dev__Role__Journalist/publications/articles/2026-02-09__state-of-the-ecosystem.md
```

This creates three problems:

1. **Discoverability:** Stakeholders must navigate GitHub's file browser to find articles. There's no table of contents, no chronological view, no category filtering.

2. **Readability:** GitHub renders markdown reasonably, but it's not optimized for long-form reading. No typography, no navigation between articles, no mobile-friendly layout.

3. **Automation gap:** The stakeholder (Dinis Cruz) wants to see the latest updates when they visit a URL -- not dig through commit logs. If the Journalist agent runs on a schedule, the site should reflect updates automatically.

---

## Proposed Solution

### Architecture

A static site generator (Jekyll or Hugo) hosted on GitHub Pages, pulling content from the Journalist's `publications/` directory.

```
Journalist commits article → GitHub Actions trigger → Static site builds → GitHub Pages serves

publications/
├── articles/          →  /articles/
├── daily-briefs/      →  /briefs/
├── interviews/        →  /interviews/
├── investigations/    →  /investigations/
└── corrections/       →  /corrections/
```

### Key Requirements

#### 1. Auto-Publish on Commit
- When the Journalist pushes to the `dev` (or `main`) branch, a GitHub Actions workflow triggers the static site build.
- The site updates within 2-3 minutes of push.
- No manual deployment step.

#### 2. Landing Page
- Shows the latest publications across all categories.
- Reverse chronological order (newest first).
- Brief summary/excerpt for each article.
- Clear publication date and category labels.

#### 3. Category Pages
- `/articles/` -- Feature articles and analysis
- `/briefs/` -- Daily and weekly briefs
- `/interviews/` -- Published interviews
- `/investigations/` -- Second-story investigations
- Each category page lists all publications in that category, newest first.

#### 4. Individual Article Pages
- Clean, readable layout (good typography, comfortable line length)
- Publication metadata (date, author, category)
- "Previous / Next" navigation
- Source attribution section
- Mobile-responsive

#### 5. RSS Feeds
- Global feed (all publications)
- Per-category feeds (articles, briefs, etc.)
- Enables stakeholders to subscribe and get notifications

#### 6. Front Matter Convention
Articles will include YAML front matter for the site generator:
```yaml
---
title: "State of the Ecosystem: Issues-FS After the Scaffolding Sprint"
date: 2026-02-09
type: feature-article
topics: [ecosystem, cli-bug, scaffolding, roadmap]
summary: "A comprehensive look at where Issues-FS stands, what's broken, and what comes next."
author: Journalist
---
```

#### 7. Minimal Design
- Focus on content, not aesthetics
- Default Jekyll theme (minima) or equivalent is fine
- Clean headers, readable body text, consistent spacing
- No custom CSS needed for v1

### What the Journalist Will NOT Build

Per the stakeholder's brief: "The journalist is *not* building the website. The journalist writes the feature request describing what it should look like."

- **Architect:** Maps the architecture, decides Jekyll vs Hugo, defines the GitHub Actions workflow
- **Dev:** Implements the site generator config, templates, and CI workflow
- **QA:** Tests the build pipeline, verifies rendering, checks mobile responsiveness
- **DevOps:** Manages GitHub Pages deployment settings

---

## Site Location Options

### Option A: In the Journalist Role Repo
- URL: `https://owasp-sbot.github.io/Issues-FS__Dev__Role__Journalist/`
- Pros: Content and site config live together. Journalist controls everything.
- Cons: Longer URL. Tied to one role repo.

### Option B: Dedicated Repo
- URL: `https://owasp-sbot.github.io/Issues-FS__News/` (new repo)
- Pros: Clean URL. Separation of concerns (content authoring vs site rendering).
- Cons: Requires cross-repo content sync.

### Option C: In the Parent Dev Repo
- URL: `https://owasp-sbot.github.io/Issues-FS__Dev/`
- Pros: Central location. Could expand to serve other role outputs (Librarian knowledge base, etc.)
- Cons: Mixes site infrastructure with development hub.

**Journalist's recommendation:** Start with **Option A** (simplest, fastest). Migrate to Option C later if the Librarian also wants a web presence.

---

## GitHub Actions Workflow (Sketch)

```yaml
name: Deploy News Site
on:
  push:
    branches: [dev, main]
    paths:
      - 'publications/**'
      - '_config.yml'

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/jekyll-build-pages@v1
        with:
          source: ./
          destination: ./_site
      - uses: actions/deploy-pages@v4
```

This is a sketch for the Architect/Dev to refine. The key constraint: it should be a standard GitHub Pages workflow, not a custom build.

---

## Content Migration Plan

### Existing Publications (Backfill)

1. Add YAML front matter to all existing articles
2. Verify markdown compatibility with chosen static site generator
3. Ensure internal links work in site context
4. Test rendering of tables, code blocks, headers

### Ongoing Process

No change to the Journalist's workflow:
1. Write article in markdown
2. Add front matter
3. `git add`, `git commit`, `git push`
4. Site auto-updates

---

## Success Criteria

1. **Stakeholder can visit a URL and see the latest articles** without navigating GitHub's file browser
2. **New articles appear on the site within 5 minutes of push** without manual intervention
3. **RSS feed works** so stakeholders can subscribe
4. **Articles are readable** on desktop and mobile
5. **No ongoing maintenance burden** -- the site just works when content is pushed

---

## Future Extensions (Not in v1)

- **Librarian knowledge base** alongside the news site
- **Search functionality** (client-side, e.g., Lunr.js)
- **Analytics** (GitHub Pages built-in or simple counter)
- **Comment system** (GitHub Discussions integration)
- **Multi-author support** (when other roles publish content)
- **Automated Journalist runs** (scheduled GitHub Action that triggers Journalist agent, generates daily brief, pushes to site)

---

## Constraints

- Must use **GitHub Pages** (public repo, free hosting)
- Must use **standard static site generator** supported by GitHub Actions (Jekyll preferred)
- Must require **zero ongoing infrastructure cost**
- Must not require stakeholders to install anything to read content
- Content must remain **readable as plain markdown** in the repo (the site is an enhancement, not a replacement)

---

*Feature request prepared by the Journalist Role*
*Issues-FS__Dev__Role__Journalist*
*Date: 2026-02-09*
