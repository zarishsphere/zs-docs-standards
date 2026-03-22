# PRD — `zs-docs-standards`

> **Document Class:** PRD | **Version:** 1.0.0 | **Status:** Bootstrapping
> **Repository:** [https://github.com/zarishsphere/zs-docs-standards](https://github.com/zarishsphere/zs-docs-standards)
> **Layer:** Layer 0 — Governance | **Catalog #:** 2
> **License:** Apache 2.0 | **Governance:** RFC-0001

---

## 1. Overview

Clinical and technical standards repository. Defines FHIR profile policies, terminology policies, clinical content standards, and interoperability requirements for the ZarishSphere platform.

---

## 2. Repository Metadata

- **Name:** `zs-docs-standards`
- **Organization:** [https://github.com/zarishsphere](https://github.com/zarishsphere)
- **Language / Runtime:** Markdown
- **Visibility:** Public
- **License:** Apache 2.0
- **Default Branch:** `main`
- **Branch Protection:** Required (2-owner review for critical paths)

---

## 3. Platform Context

This repository is part of the **ZarishSphere** sovereign digital health operating platform — a free, open-source, FHIR R5-native system for South and Southeast Asia.

**Non-negotiable constraints:**
- Zero cost — all tooling must use genuinely free tiers
- FHIR R5 native — all clinical data modelled as FHIR R5 resources
- Offline-first — must work without network connectivity
- No-coder friendly — GUI-first, template-driven
- Documentation as Code — all decisions in GitHub

---

## 4. Goals & Objectives

- Define FHIR R5 profiling conventions for ZarishSphere
- Establish terminology governance (ICD-11, SNOMED, LOINC, CIEL)
- Document clinical content quality standards
- Provide policy for form validation and JSON Schema conventions

## 5. Functional Requirements

| ID | Requirement | Priority |
|----|------------|---------|
| F-01 | FHIR R5 profiling policy and ZarishSphere IG conventions | P0 |
| F-02 | Terminology governance policy for ICD-11, SNOMED, LOINC, CIEL | P0 |
| F-03 | Clinical form JSON Schema standards (ZS Form Schema v1) | P0 |
| F-04 | FHIR mapping requirements for all clinical fields | P0 |
| F-05 | i18n key naming conventions for translations | P1 |
| F-06 | HIPAA/GDPR data classification policy | P1 |
| F-07 | API design standards (OpenAPI 3.1, RESTful conventions) | P1 |
| F-08 | Event schema standards (AsyncAPI 3.0, NATS topics) | P2 |

## 6. Repository Tree

```
zs-docs-standards/
├── README.md
├── LICENSE
├── .github/
│   ├── CODEOWNERS
│   └── workflows/
│       └── ci.yml
├── fhir/
│   ├── FHIR-PROFILING-POLICY.md       # How to create ZS StructureDefinitions
│   ├── FHIR-R5-CONVENTIONS.md         # ZS-specific FHIR R5 rules
│   ├── FHIR-R4-BRIDGE-POLICY.md       # When and how to use R4 bridge
│   ├── FHIR-SEARCH-STANDARDS.md       # Required search parameters per resource
│   └── FHIR-AUDIT-POLICY.md           # AuditEvent requirements (HIPAA)
├── terminology/
│   ├── TERMINOLOGY-GOVERNANCE.md      # Master terminology policy
│   ├── ICD11-USAGE.md                 # ICD-11 coding standards
│   ├── SNOMED-USAGE.md                # SNOMED CT binding rules
│   ├── LOINC-USAGE.md                 # LOINC code requirements for observations
│   ├── CIEL-USAGE.md                  # OpenMRS CIEL concept policy
│   └── TERMINOLOGY-UPDATE-PROCESS.md  # How/when to update terminology data
├── clinical-content/
│   ├── FORM-SCHEMA-SPEC.md            # ZS Form Schema v1 specification
│   ├── FORM-VALIDATION-RULES.md       # JSON Schema validation requirements
│   ├── FHIR-MAPPING-REQUIREMENTS.md   # Every field must have fhirPath
│   ├── I18N-KEY-CONVENTIONS.md        # Translation key naming rules
│   ├── CLINICAL-QUALITY-GATES.md      # What a form must have before merge
│   └── FORM-VERSIONING-POLICY.md      # Semver for clinical forms
├── api/
│   ├── OPENAPI-CONVENTIONS.md         # OpenAPI 3.1 standards
│   ├── REST-DESIGN-GUIDE.md           # RESTful API design rules
│   ├── ASYNCAPI-CONVENTIONS.md        # AsyncAPI 3.0 event schema standards
│   ├── ERROR-RESPONSE-FORMAT.md       # Standard error envelope
│   └── PAGINATION-STANDARDS.md        # FHIR bundle pagination rules
├── security/
│   ├── DATA-CLASSIFICATION.md         # PHI, PII, operational data tiers
│   ├── GDPR-COMPLIANCE.md             # GDPR controls documentation
│   ├── HIPAA-CONTROLS.md              # HIPAA audit trail requirements
│   └── SMART-ON-FHIR-POLICY.md       # SMART 2.1 scope requirements
└── infrastructure/
    ├── NAMING-CONVENTIONS-K8S.md      # Kubernetes resource naming
    ├── HELM-CHART-STANDARDS.md        # Helm chart structure requirements
    └── DOCKER-IMAGE-POLICY.md         # Image naming, tagging, scanning
```

## 7. Key Interfaces

- Referenced by all `zs-content-forms-*` and `zs-data-*` repositories
- Enforced by `zs-agent-content-validator` on every PR
- Consumed by `zs-agent-code-review` for FHIR compliance checks

## 9. Ownership & Governance

| Role | GitHub User |
|------|-------------|
| Platform Lead | `@arwa-zarish` |
| Technical Lead | `@code-and-brain` |
| DevOps Lead | `@DevOps-Ariful-Islam` |
| Health Programs | `@BGD-Health-Program` |

All changes go through Pull Request → 1+ owner review → CI pass → merge.
Breaking changes require RFC + ADR.

---

## 10. Definition of Done

- [ ] All listed files exist with content
- [ ] CI pipeline passes (test + lint + security)
- [ ] README.md reflects current state
- [ ] OpenAPI / AsyncAPI spec present (services only)
- [ ] At least 1 integration test using testcontainers-go (Go) or Playwright (UI)
- [ ] No secrets committed (GitGuardian verified)
- [ ] CODEOWNERS file present
- [ ] Linked to CATALOGS.md and TODO.md

---

*This PRD is the canonical source of truth for this repository's purpose, structure, and requirements.*
*Changes require a PR against this file with owner approval.*
