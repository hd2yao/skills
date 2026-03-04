---
name: hd2yao-feature-requirement-ideation
description: Use when starting a new feature and requirements are ambiguous; clarifies goals, scope, constraints, and acceptance criteria before writing plans or code.
---

# HD2YAO Feature Requirement Ideation

## Overview

Clarify what should be built before planning or implementation.

**Announce at start:** "I'm using hd2yao-feature-requirement-ideation to clarify feature requirements."

## Process

1. Collect context from user request and current project state.
2. Clarify goals, scope boundaries, constraints, and success criteria.
3. Identify assumptions and open questions explicitly.
4. Produce a discovery document in the current repository root.
5. Ask for confirmation before moving to technical planning.

## Output

Save to: `./<feature>.discovery.md`

Use this structure:

```markdown
# <Feature> Discovery

## Problem Statement

## Goals

## Non-Goals

## Target Users and Scenarios

## Constraints
- Technical
- Product
- Timeline

## Assumptions

## Acceptance Criteria

## Open Questions
```

## Quality Gate

Do not hand off to planning until:
- Scope and non-goals are explicit.
- Acceptance criteria are testable.
- Open questions are either resolved or tracked.

## Handoff

When approved, invoke `hd2yao-feature-tech-plan-planmode`.
