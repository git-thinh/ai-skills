---
name: spec_constitution_en
description: Establish or amend the binding project constitution for a software repository. Use when invoked through /spec_constitution_en or @spec_constitution_en with a project description, stack, architecture, coding conventions, security, testing, performance or organizational constraints. Automatically select Initialize or Amend based on whether ./spec/01.constitution.md exists.
---

# Project Constitution

## Input and authority
- Receive the complete user argument string following `/spec_constitution_en` or `@spec_constitution_en`.
- Operate in the current project root (not the skill installation directory).
- The single canonical output is `./spec/01.constitution.md`.
- Treat user instructions as requested policy, existing constitution as binding baseline in Amend, and repository facts as evidence. Never pretend a dependency or configuration exists without inspection.

## Workflow
1. Locate project root using the current workspace; inspect `package.json`, lockfiles, framework configs, source layout, README, test/lint/CI configurations and existing project instructions as available. Avoid scanning generated folders or secrets. Do not install dependencies or change application code.
2. Check whether `./spec/01.constitution.md` exists before writing anything. If absent, select **Initialize**; if present, select **Amend**. A zero-byte or malformed existing file still counts as Amend: preserve it and request clarification if safe interpretation is impossible.
3. Parse the user's description into explicit requirements, inferred recommendations, unknowns and conflicts. Verify existing project technology from files. Explicit user requirements outrank generic defaults, but identify clashes with current configuration.
4. In Initialize, draft a complete, concrete constitution using `CONSTITUTION-TEMPLATE`. Create `spec/` if necessary. Avoid overly prescriptive rules unsupported by user intent or repository evidence; label proposed defaults.
5. In Amend, read the entire existing constitution, retain unrelated principles and numbering, update only relevant clauses, explain conflicts and migration implications, and never silently weaken security/testing guarantees. If the request is ambiguous or breaks a foundational principle, ask for approval before replacing that principle.
6. Version with semantic versioning: Initialize at 1.0.0; Amend PATCH for clarifications, MINOR for additive rules, MAJOR for removal or incompatible changes. Record updated date and concise amendment history; preserve the original ratified date.
7. Check that every MUST is testable or has a measurable review criterion; eliminate contradictory requirements and technology assumptions. Verify output path, headings, and actual file content after writing.
8. Report selected mode, file path, version, changed principles, assumptions and any unresolved conflicts. Do not claim success unless the file was written and verified.

## Required domains
Include project purpose/scope; architecture and boundaries; stack and dependencies; folder organization; naming and coding conventions; security/privacy/secrets; test strategy and TDD policy; performance/accessibility where applicable; quality gates; AI-agent operating rules; governance and amendment procedure. Use explicit MUST/SHOULD/MAY language. Tailor sections to the user and actual project.

## Safety
Never overwrite existing text with a generic template in Amend. Do not access secrets or exfiltrate repository contents. Never add dependencies, refactor source code, or modify unrelated files. Ask only when necessary to resolve high-impact ambiguity.

## CONSTITUTION-TEMPLATE

```text

# Project Constitution

**Version:** 1.0.0  
**Ratified:** YYYY-MM-DD  
**Last amended:** YYYY-MM-DD  
**Status:** Active

## 1. Mission and Scope
- Define product goal, supported platforms and out-of-scope work.

## 2. Architecture Principles
- Define architecture, separation of concerns, state ownership and module boundaries.

## 3. Technology Stack
- List verified runtime/framework/styling/build tools and upgrade policy.

## 4. Repository Structure
- Describe directories and ownership boundaries without inventing files.

## 5. Code Standards
- Specify naming, typing, formatting, error handling and maintainability rules.

## 6. Security and Privacy
- Specify input validation, authentication as applicable, dependency and secret management.

## 7. Testing and Quality
- Define unit/integration/e2e scope, TDD expectations and mandatory checks.

## 8. Performance and Accessibility
- Set context-appropriate targets and measurement methods.

## 9. AI Agent Rules
- Require reading this constitution before planning or implementation; honor existing conventions, avoid unrequested changes, and report deviations.

## 10. Governance
- Constitution supersedes ordinary implementation preferences, subject to higher-priority instructions. Amend with documented rationale, impact assessment, version increment and change log.

## Amendment History
| Date | Version | Change | Reason |
|---|---|---|---|
| YYYY-MM-DD | 1.0.0 | Initial ratification | Project initialization |

```