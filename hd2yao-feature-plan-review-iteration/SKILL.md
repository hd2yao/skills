---
name: hd2yao-feature-plan-review-iteration
description: Use when a feature plan needs review feedback incorporated through versioned document updates until blocking comments are resolved.
---

# HD2YAO Feature Plan Review Iteration

## Overview

Iterate plan documents based on review feedback with strict traceability.

**Announce at start:** "I'm using hd2yao-feature-plan-review-iteration to process review feedback and iterate the plan."

<HARD-GATE>
Do not finish this skill with chat-only feedback. You MUST write the next plan version to disk and verify it exists before handoff.
</HARD-GATE>

## Process

1. Load the latest plan version: `./<feature>.plan.vN.md`.
2. Gather feedback from user/reviewer.
3. Classify feedback as Blocking, Important, or Minor.
4. Update the plan and prepare the next version content.
5. Write the next version to disk as `./<feature>.plan.vN+1.md`.
6. Verify persistence with `test -f ./<feature>.plan.vN+1.md`.
7. Record each comment and disposition in the review log.
8. Report the saved file path and repeat until no blocking comments remain.

## Output

Save to: `./<feature>.plan.vN+1.md`

Include this section:

```markdown
## Review Log

| ID | Severity | Comment | Decision | Notes | Status |
|----|----------|---------|----------|-------|--------|
```

## Mandatory Persistence Rule

- Every review iteration must create a new versioned plan file on disk.
- Chat-only review summaries do not satisfy this skill's output requirement.
- If file write or verification fails, report the blocker and stop. Do not hand off.

## Quality Gate

Implementation can start only when:
- Blocking comments count is 0.
- Important comments are resolved or explicitly deferred.
- Decisions are documented in the review log.
- The latest `./<feature>.plan.vN+1.md` file exists on disk and its path has been reported.

## Single-Use Mode

If user asks for one pass only, run one iteration and stop.

## Handoff

When approved, invoke `hd2yao-feature-implementation-delivery`.
