# Routes and Links

## Route Table

| Page                  | Route                                   | Source                      |
| --------------------- | --------------------------------------- | --------------------------- |
| Public Homepage       | `/`                                     | `index.html`                |
| Login / Role Selector | `/login.html`                           | `login.html`                |
| Employee Home         | `/employee/`                            | `employee/index.html`       |
| Assessment            | `/employee/assessment.html`             | `employee/assessment.html`  |
| Marketplace           | `/employee/marketplace.html`            | `employee/marketplace.html` |
| Activity Detail       | `/employee/detail.html?id=<activityId>` | `employee/detail.html`      |
| HR Dashboard          | `/hr/dashboard.html`                    | `hr/dashboard.html`         |

## Required Links

### From Login

```txt
Employee Demo -> /employee/
HR Demo -> /hr/dashboard.html
Executive Demo -> /hr/dashboard.html
```

### From App Shell Profile Menu

```txt
Switch Account -> /login.html
```

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
