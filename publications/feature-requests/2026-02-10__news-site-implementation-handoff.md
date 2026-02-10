# Implementation Handoff: Issues-FS News Site (GitHub Pages)

**From:** Journalist Role
**To:** Architect Role (architecture decisions), Dev Role (implementation)
**Date:** 2026-02-10
**Source:** [Feature Request: GitHub Pages News Site](2026-02-09__github-pages-news-site.md)
**Type:** Handoff

---

## Summary

The Journalist role has produced a feature request for a GitHub Pages news site. This handoff asks the Architect and Dev roles to review the request and produce an implementation brief covering architecture decisions, technical scope, and timeline.

A stakeholder voice interview is being conducted via ChatGPT to gather additional input on vision, audience, and technical preferences. The interview transcript will be available at `publications/interviews/2026-02-10__stakeholder-interview-dinis-cruz.md` once completed. The implementation brief can proceed in parallel -- the interview may refine preferences but the core requirements are clear.

---

## What the Journalist Has Defined

### Requirements (from the feature request)
1. Static site on GitHub Pages, auto-publishes on push
2. Landing page with latest publications (reverse chronological)
3. Category pages: `/articles/`, `/briefs/`, `/interviews/`, `/investigations/`, `/corrections/`
4. Individual article pages with clean typography and navigation
5. RSS feeds (global + per-category)
6. YAML front matter convention for metadata
7. Minimal design (content-first, default theme acceptable for v1)
8. Zero ongoing infrastructure cost

### Content Structure (already in place)
```
publications/
├── articles/          (1 article exists)
├── feature-requests/  (this document + the original request)
├── interviews/        (2 interview docs exist)
├── daily-briefs/      (planned, not yet populated)
├── investigations/    (planned)
└── corrections/       (planned)
```

### Site Location Recommendation
Option A: In the Journalist Role Repo (`Issues-FS__Dev__Role__Journalist`)
- URL: `https://owasp-sbot.github.io/Issues-FS__Dev__Role__Journalist/`
- Journalist controls content and site config together
- Simplest to implement, can migrate later if needed

### Existing CI Sketch (from feature request)
```yaml
name: Deploy News Site
on:
  push:
    branches: [dev, main]
    paths: ['publications/**', '_config.yml']
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/jekyll-build-pages@v1
      - uses: actions/deploy-pages@v4
```

---

## What the Architect Needs to Decide

1. **Static site generator:** Jekyll (GitHub Pages native, simpler) vs Hugo (faster builds, richer features, needs custom action). The Journalist recommends Jekyll for v1 simplicity.

2. **Content mapping:** How do `publications/` subdirectories map to site routes? Direct mirror, or restructured for Jekyll/Hugo conventions (e.g., `_posts/` for Jekyll)?

3. **Theme:** Jekyll minima (default) or a different minimal theme? Must be mobile-responsive.

4. **Front matter schema:** Standardize the YAML fields that all publications must include. The Journalist proposed: `title`, `date`, `type`, `topics`, `summary`, `author`.

5. **Feed architecture:** Single RSS feed vs per-category feeds vs both. Technical approach (Jekyll plugin vs manual).

6. **URL structure:** `/{category}/{slug}` or `/{date}/{slug}` or `/{category}/{date}/{slug}`?

7. **Build trigger scope:** Build on all pushes to `dev`/`main`, or only when `publications/` or `_config.yml` change?

8. **Future extensibility:** If other roles want web presence later (Librarian knowledge base, Cartographer maps), does that change the v1 architecture?

---

## What the Dev Needs to Implement

Once the Architect decides, the Dev scope includes:

1. **Jekyll/Hugo configuration** -- `_config.yml` or `config.toml` with site metadata, theme, permalink structure, feed plugin
2. **Layout templates** -- Landing page, category pages, article pages (may be default theme with minor customization)
3. **GitHub Actions workflow** -- Build and deploy pipeline
4. **Content migration** -- Add YAML front matter to existing publications, verify rendering
5. **GitHub Pages setup** -- Enable Pages in repo settings, configure source branch/directory
6. **Testing** -- Verify build locally, test mobile rendering, validate RSS feeds

### Known Constraints
- PAT needs `workflow` scope for pushing `.github/workflows/` (noted in project memory)
- The Journalist repo is a git submodule of `Issues-FS__Dev` -- GitHub Pages may need to be configured at the individual repo level
- Content must remain readable as plain markdown in the repo (the site is an enhancement, not a replacement)

---

## Requested Deliverable

**From Architect:** An Architecture Decision Record (ADR) covering:
- Chosen static site generator and rationale
- URL structure and content mapping
- Feed architecture
- Theme selection
- Deployment architecture
- Future extensibility considerations

**From Dev:** An implementation plan covering:
- Task breakdown with effort estimates
- File list (configs, templates, workflows)
- Migration steps for existing content
- Testing checklist
- Definition of done

---

## Timeline Context

- **Priority:** P2 (per original feature request -- after CLI fix and foundation hardening)
- **CLI fix:** Shipped (2026-02-10)
- **Dependency:** None blocking. This can start now.
- **Stakeholder interview:** In progress via ChatGPT voice mode. Technical preferences may refine the brief.

---

*Handoff prepared by Journalist Role | Issues-FS__Dev__Role__Journalist*
