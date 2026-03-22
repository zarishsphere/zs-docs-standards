# PRD-MVP — `zs-docs-standards`

> **Document:** Product Requirements (MVP) | **Version:** 1.0.0-mvp
> **Repository:** [https://github.com/zarishsphere/zs-docs-standards](https://github.com/zarishsphere/zs-docs-standards)
> **Layer:** Layer 0 — Governance | **Catalog #:** 2
> **Language:** Markdown | **License:** Apache 2.0

---

## Executive Summary

**Clinical and technical standards repository — FHIR profiling policy, terminology governance, and ZS Form Schema v1.**

This document defines the **Minimum Viable Product (MVP)** scope for `zs-docs-standards` within the ZarishSphere sovereign digital health platform. It covers what must be built first, acceptance criteria, user stories, and the complete repository file structure.


### Platform Non-Negotiables (apply to every repository)

| Constraint | Rule |
|-----------|------|
| **Zero Cost** | All tooling, hosting, and services must use genuinely free tiers |
| **Open Source** | Apache 2.0 license; all code public |
| **FHIR R5 Native** | All clinical data modelled as FHIR R5 resources |
| **Offline-First** | Must function without network connectivity |
| **No-Coder Friendly** | GUI-first, template-driven, automatable |
| **Documentation as Code** | All decisions in GitHub via RFC/ADR |
| **Multi-tenant** | tenant_id scoping on all data operations |
| **HIPAA/GDPR** | AuditEvent on all PHI access; field-level encryption |

---

## Problem Statement

Without this repository, platform contributors and country program teams lack the governance documentation they need. Decisions become tribal knowledge, standards are inconsistently applied, and the platform cannot scale across countries.

## MVP Goals

1. ZS Form Schema v1 specification published
2. FHIR profiling policy defined
3. Terminology governance policy for ICD-11, SNOMED, LOINC, CIEL

## MVP Functional Requirements

| ID | Requirement | Acceptance Criteria | Priority |
|----|------------|---------------------|---------|
| M-01 | ZS Form Schema v1 JSON Schema published | schemas/zs-form-schema-v1.json is valid JSON Schema | P0 |
| M-02 | FHIR-PROFILING-POLICY.md written | File exists with at least profiling rules | P0 |
| M-03 | TERMINOLOGY-GOVERNANCE.md written | File covers all 6 terminology systems | P0 |
| M-04 | FORM-SCHEMA-SPEC.md written | Full field reference documented | P0 |
| M-05 | OpenAPI conventions documented | REST conventions cover ZarishSphere patterns | P1 |

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
