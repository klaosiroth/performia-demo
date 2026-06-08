# AGENTS.md — Performia Static Demo

## Project Goal

This repository is a static HTML demo prototype for Performia.

The goal is to prepare a customer-facing demo website from existing HTML sources.

This is NOT a production application yet.

## Important Rules

- Do not rewrite the UI from scratch.
- Do not convert the project to React, Next.js, Vue, or any framework.
- Keep the existing visual design, layout, typography, colors, and interactions as close as possible to the original HTML files.
- Only make changes needed to:
  - reorganize files
  - fix navigation links
  - connect pages together
  - add mock demo state
  - improve static deploy compatibility
- Do not add real authentication.
- Do not add database integration.
- Do not add Supabase, Firebase, Prisma, or any backend service.
- Do not introduce a build step unless explicitly requested.
- This project must remain deployable as plain static HTML/CSS/JS.

## Source Files

The original source files are located in:

/source

The agent is responsible for:

1. Moving files into final locations
2. Renaming files
3. Updating internal navigation
4. Updating relative paths
5. Preserving UI and behavior

## Source Files Mapping

Map the original source files as follows:

- `performia-login-v8.html` → `index.html`
- `performia-employee-home.html` → `employee/index.html`
- `performia-assessment.html` → `employee/assessment.html`
- `performia-marketplace.html` → `employee/marketplace.html`
- `performia-detail.html` → `employee/detail.html`
- `hr-dashboard.html` → `hr/dashboard.html`

## Portal Separation

There are two portals:

### Employee Portal

Base path:

```txt
/employee/
```

Pages:

```txt
/employee/index.html
/employee/assessment.html
/employee/marketplace.html
/employee/detail.html
```

### HR Portal

Base path:

```txt
/hr/
```

Pages:

```txt
/hr/dashboard.html
```

## Login Behavior

The root `index.html` acts as a demo login / role selector.

Expected redirects:

```js
employee  -> /employee/
hr        -> /hr/dashboard.html
executive -> /hr/dashboard.html
```

Store selected role in localStorage:

```js
localStorage.setItem("performia_demo_role", role);
```

## Mock Data

Use static mock data only.

Preferred shared mock data file:

```txt
/assets/mock-data.js
```

Expose data on:

```js
window.PERFORMIA_DEMO;
```

Do not fetch remote APIs.

## Demo State

Use localStorage for demo-only state.

Suggested keys:

```txt
performia_demo_role
performia_demo_lang
performia_demo_assessment_done
performia_demo_bookings
```

## Navigation Rules

All links must work after static deployment.

Use root-relative links:

```txt
/
 /employee/
 /employee/assessment.html
 /employee/marketplace.html
 /employee/detail.html?id=<activityId>
 /hr/dashboard.html
```

Do not use local filesystem paths.

Do not link to the original source filenames after migration.

Bad:

```txt
performia-marketplace.html
performia-detail.html
hr-dashboard.html
```

Good:

```txt
/employee/marketplace.html
/employee/detail.html
/hr/dashboard.html
```

## Acceptance Criteria

The demo must support this flow:

1. Open `/`
2. Select Employee Demo
3. Land on `/employee/`
4. Navigate to assessment
5. Complete or simulate assessment
6. Navigate to marketplace
7. Open activity detail
8. Simulate booking success
9. Return to employee home
10. Return to `/`
11. Select HR Demo
12. Land on `/hr/dashboard.html`

## Quality Bar

Before finishing, verify:

- No broken internal links
- No references to old source filenames
- Employee and HR portals are separated
- Static deployment works without build tools
- UI remains visually consistent with original source
- Browser console has no critical JavaScript errors
