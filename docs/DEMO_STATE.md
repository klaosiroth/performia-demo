# Performia Demo State Contract

This document defines localStorage state used by the static Performia demo.

The demo uses client-only state. Do not add backend calls, remote persistence, authentication, databases, or API writes for this state.

## Shared Language

Key:

```txt
performia_demo_lang
```

Allowed values:

- `th`
- `en`

Rules:

- All runtime pages that support language switching must read and write this key.
- The selected language must persist across Login Shell, App Shell, and Focused Flow Shell pages.
- Invalid values must fall back safely to Thai (`th`) or the page default.

## Assessment Completion

Key:

```txt
performia_demo_assessment_done
```

Allowed values:

- `"true"`
- absent or `"false"`

Rules:

- Completing the assessment sets `performia_demo_assessment_done` to `"true"`.
- Pages may treat absent, malformed, or `"false"` as not completed.
- Completion is demo-only state and must remain in localStorage.

## Assessment Progress

Key:

```txt
performia_demo_assessment_progress
```

JSON shape:

```json
{
  "version": 1,
  "status": "in_progress",
  "currentIndex": 0,
  "answers": {},
  "updatedAt": "ISO-8601 timestamp"
}
```

Rules:

- Save & Exit stores `currentIndex`, `answers`, `status`, `version`, and `updatedAt`.
- Save & Exit redirects to `/employee/`.
- Opening assessment restores valid in-progress state.
- Invalid or malformed saved state falls back safely to a new assessment.
- Completing assessment sets `performia_demo_assessment_done` to `"true"`.
- Completing assessment removes `performia_demo_assessment_progress`.
- Language changes must not reset assessment progress.
- Do not add backend calls or remote persistence.

## Employee Home Assessment CTA

State behavior:

- Not started -> Start Assessment
- In progress -> Continue Assessment
- Completed -> View Results or View Recommended Activities

Rules:

- Use the current page language for CTA labels.
- CTA state should be derived from `performia_demo_assessment_done` and `performia_demo_assessment_progress`.
- Invalid or malformed progress should be treated as not started unless completion is `"true"`.
