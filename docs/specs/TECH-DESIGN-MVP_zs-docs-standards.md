# TECH-DESIGN-MVP — `zs-docs-standards`

> **Document:** Technical Design (MVP) | **Version:** 1.0.0-mvp
> **Repository:** [https://github.com/zarishsphere/zs-docs-standards](https://github.com/zarishsphere/zs-docs-standards)
> **Layer:** Layer 0 — Governance | **Catalog #:** 2
> **Language:** Markdown / Docusaurus (future) | **License:** Apache 2.0

---

## Technical Summary

**Clinical and technical standards repository — FHIR profiling policy, terminology governance, and ZS Form Schema v1.**

This document defines the **technical architecture, implementation design, complete repository tree, and acceptance criteria** for the MVP of `zs-docs-standards`.

---

## Technical Approach — MVP

All MVP content is **pure Markdown** — no build tooling, no dependencies. Files are browseable directly on GitHub. Docusaurus is a **post-MVP** addition.

## File Format Standards

- All files: UTF-8 encoding, Unix line endings (LF)
- Headings: ATX style (`#`, `##`, `###`)
- Tables: GFM pipe tables
- Code blocks: fenced with language tag
- Links: relative paths within repo; absolute for cross-repo

## CI Pipeline (`.github/workflows/ci.yml`)

```yaml
name: CI
on: [push, pull_request]
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: markdownlint
        run: npx markdownlint-cli "**/*.md" --ignore node_modules
      - name: Check links (MVP only internal)
        run: npx markdown-link-check docs/**/*.md --config .mlc.json
```

## Content Governance

The ZS Form Schema v1 is the most critical artifact. It is a JSON Schema 2020-12 meta-schema that all clinical forms must validate against.

## Directory Naming Convention

- `docs/` — user-facing documentation
- `templates/` — reusable templates for contributors
- `governance/` — process definitions (RFC, ADR, CAMM)
- `compliance/` — regulatory documentation

## MVP Complete Repository Tree

```
zs-docs-standards/
├── README.md
├── LICENSE
├── .github/
│   ├── CODEOWNERS
│   └── workflows/
│       └── ci.yml
├── fhir/
│   ├── FHIR-PROFILING-POLICY.md
│   ├── FHIR-R5-CONVENTIONS.md
│   └── FHIR-AUDIT-POLICY.md
├── terminology/
│   ├── TERMINOLOGY-GOVERNANCE.md
│   ├── ICD11-USAGE.md
│   ├── SNOMED-USAGE.md
│   ├── LOINC-USAGE.md
│   └── CIEL-USAGE.md
├── clinical-content/
│   ├── FORM-SCHEMA-SPEC.md
│   ├── FORM-VALIDATION-RULES.md
│   └── I18N-KEY-CONVENTIONS.md
├── api/
│   ├── OPENAPI-CONVENTIONS.md
│   └── REST-DESIGN-GUIDE.md
└── schemas/
    └── zs-form-schema-v1.json
```

---


## Owners & Governance

| Role | GitHub Handle | Responsibility |
|------|--------------|----------------|
| Platform Lead | `@arwa-zarish` | Final approval, RFC votes |
| Technical Lead | `@code-and-brain` | Architecture, Go/TS review |
| DevOps Lead | `@DevOps-Ariful-Islam` | CI/CD, infra, deployment |
| Health Programs | `@BGD-Health-Program` | Clinical content, country programs |

**PR Policy:** All changes via Pull Request. Minimum 1 owner review. CI must pass. No direct commits to `main`.


---

## MVP Acceptance Checklist

- [ ] All MVP files exist in repository with real content (not placeholders)
- [ ] CI pipeline passes on `main` branch
- [ ] No secrets, credentials, or PHI committed
- [ ] README.md reflects current state with setup instructions
- [ ] CODEOWNERS file present
- [ ] All MVP functional requirements verified manually or via automated tests
- [ ] Linked to `CATALOGS.md` and `TODO.md` in `zs-docs-platform`

---

*This document is the authoritative MVP specification for `zs-docs-standards`.*
*Changes require a Pull Request with at least 1 owner approval.*
