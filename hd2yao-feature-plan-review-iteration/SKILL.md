---
name: hd2yao-feature-plan-review-iteration
description: Use when a feature plan needs review feedback incorporated through versioned document updates until blocking comments are resolved.
---

# HD2YAO Feature Plan Review Iteration

## Overview

Iterate plan documents based on review feedback with strict traceability.

**Announce at start:** "I'm using hd2yao-feature-plan-review-iteration to process review feedback and iterate the plan."

## Process

1. Load the latest plan version: `./<feature>.plan.vN.md`.
2. Gather feedback from user/reviewer.
3. Classify feedback as Blocking, Important, or Minor.
4. Update the plan and produce the next version.
5. Record each comment and disposition in the review log.
6. Repeat until no blocking comments remain.

## Output

Save to: `./<feature>.plan.vN+1.md`

Include this section:

```markdown
## Review Log

| ID | Severity | Comment | Decision | Notes | Status |
|----|----------|---------|----------|-------|--------|
```

## Quality Gate

Implementation can start only when:
- Blocking comments count is 0.
- Important comments are resolved or explicitly deferred.
- Decisions are documented in the review log.

## Single-Use Mode

If user asks for one pass only, run one iteration and stop.

## Handoff

When approved, invoke `hd2yao-feature-implementation-delivery`.
