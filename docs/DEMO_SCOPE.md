# Demo Scope

## Purpose

This is a customer-facing MVP demo for Performia.

The demo should make the product feel connected and clickable without using a real database.

## In Scope

- Static HTML page organization
- Employee portal
- HR portal
- Working links between pages
- Demo login role selection
- Shared mock data
- localStorage demo state
- Static deploy readiness
- Minor bug fixes required for navigation

## Out of Scope

- Real authentication
- Real authorization
- Real employee data
- Database schema
- Supabase integration
- API server
- Payment
- Admin CRUD
- Real report generation
- Full frontend framework migration
- Pixel-perfect redesign
- Large UI refactor

## Demo Narrative

The customer should understand this story:

1. Employee logs in.
2. Employee sees My Performia dashboard.
3. Employee completes PERFORM-6 assessment.
4. Employee receives personal insight and recommended activities.
5. Employee browses marketplace.
6. Employee books an activity.
7. HR sees aggregated organization-level insights only.

## Privacy Positioning

This demo must communicate that:

- Employee individual answers are private.
- HR sees aggregated insights.
- Demo data is mock data.
- No real employee data is stored.

`````

---

## 3. `docs/ROUTES_AND_LINKS.md`

ไฟล์นี้ช่วยให้ Codex แก้ลิงก์อย่างเป็นระบบ

````md
# Routes and Links

## Route Table

| Page | Route | Source |
|---|---|---|
| Login / Role Selector | `/` | `index.html` |
| Employee Home | `/employee/` | `employee/index.html` |
| Assessment | `/employee/assessment.html` | `employee/assessment.html` |
| Marketplace | `/employee/marketplace.html` | `employee/marketplace.html` |
| Activity Detail | `/employee/detail.html?id=<activityId>` | `employee/detail.html` |
| HR Dashboard | `/hr/dashboard.html` | `hr/dashboard.html` |

## Required Links

### From Login

```txt
Employee Demo -> /employee/
HR Demo -> /hr/dashboard.html
Executive Demo -> /hr/dashboard.html
`````

### From Employee Home

```txt
Assessment CTA -> /employee/assessment.html
Marketplace CTA -> /employee/marketplace.html
Activity CTA -> /employee/detail.html?id=sleep-reset
```

### From Assessment

```txt
Back/Home -> /employee/
Recommended Activities -> /employee/marketplace.html?recommended=true
```

### From Marketplace

```txt
Activity Card -> /employee/detail.html?id=<activityId>
Sidebar Home -> /employee/
Sidebar Assessment -> /employee/assessment.html
Sidebar Activities -> /employee/marketplace.html
```

### From Detail

```txt
Back -> /employee/marketplace.html
Booking Success Continue -> /employee/
View More Activities -> /employee/marketplace.html
```

### From HR Dashboard

```txt
Logo/Home -> /hr/dashboard.html
```

## Link Requirements

- Use root-relative paths.
- Do not use absolute external URLs for internal navigation.
- Do not use old filenames.
- Query string IDs are allowed for activity demo pages.
