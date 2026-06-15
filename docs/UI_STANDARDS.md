# Performia Static Demo UI Standards

This document defines the shared UI standards for the Performia static HTML demo. Use it as the source of truth before making UI changes.

The standards preserve the current prototype direction: plain static HTML/CSS/JS, no framework migration, no build step, and no runtime backend.

# Shell Architecture Rules

The Performia demo uses three shell types.

These shells are intentionally different and must not be merged.

## Login Shell

Pages:

- `login.html`

Purpose:

- Demo login.
- Role selection.
- Demo portal entry after the public homepage.

Standards:

- Custom layout allowed.
- Floating language switch allowed.
- No sidebar.
- No app-shell header.
- Logo may use:
  - `/assets/logo-white.png` on dark navy surfaces.
  - `/assets/logo-color.png` on light surfaces.

Do not force Login Shell to match App Shell.

## App Shell

Pages:

- `employee/index.html`
- `employee/marketplace.html`
- `employee/detail.html`
- `hr/dashboard.html`

Canonical Reference:

- `employee/marketplace.html`

All App Shell pages should align to marketplace shell behavior.

Required Standards:

- Sidebar width = `260px`.
- Header height = `72px`.
- Desktop content padding = `32px`.
- Mobile content padding = `16px` to `20px`.
- Content max width = `1440px`.

Language:

- Segmented `TH / EN` control.
- State key = `performia_demo_lang`.

Profile:

- Header avatar always opens profile menu.

Logo:

- Desktop logo height = `40px`.
- `logo-color` on light surfaces.
- `logo-white` on dark surfaces.

Navigation:

- Consistent nav item behavior.
- Consistent active state.
- Consistent hover state.

App Shell pages may differ in:

- Page content.
- Cards.
- Dashboard metrics.
- HR-specific sections.

## Focused Flow Shell

Pages:

- `employee/assessment.html`

Purpose:

- Assessment experience.
- Minimize distractions.
- Single-task flow.

Required Standards:

- No sidebar.
- Sticky header.
- Header height = `56px`.
- Content width = `720px` to `760px`.
- Compact spacing.

Language:

- Uses the shared segmented `TH / EN` control.
- Language state uses `performia_demo_lang`.
- The selected language must persist across all runtime pages.
- May place the segmented control in the compact focused header.

Do not force Focused Flow Shell to match App Shell.

Specifically:

- Do not add sidebar.
- Do not use `72px` app header.
- Do not copy marketplace layout.
- Do not convert assessment into App Shell.

# Shared UI Standards

## Brand Tokens

Use these tokens as the default app-wide values:

```css
:root {
  --navy: #071B63;
  --navy-dark: #031244;
  --aqua: #10D5D2;
  --cyan: #59E3FF;
  --text-primary: #061849;
  --text-secondary: #52627A;
  --background: #F8FBFD;
  --border: #DCEAF5;
  --font: "Noto Sans Thai", sans-serif;
}
```

Avoid introducing alternate navy/aqua/background/border values unless preserving an existing source page requires it. If a page already uses close variants, prefer aligning new work to the tokens above.

## Logo Rules

Use the image logo as the standard logo implementation.

- Use `/assets/logo-color.png` for light surfaces.
- Use `/assets/logo-white.png` for dark navy surfaces.
- Desktop logo height: `40px`.
- Recommended image style:

```html
<img src="/assets/logo-color.png" alt="Performia" style="width:auto;height:40px;display:block;" />
```

Do not duplicate a text logo beside the image logo. For example, do not render the logo image and an extra visible `Performia` wordmark next to it.

Do not introduce new text-only logo marks in runtime pages. Existing CSS-only logo mark definitions should be treated as legacy unless they are actively rendered as fallback UI.

## App Shell Standards

For app shell pages, use:

- Sidebar width: `260px`.
- Header height: `72px`.
- Content padding: `32px` on desktop.
- Content padding on mobile/tablet: `16px` to `20px`.
- Content max width: `1440px`.
- Page background: `#F8FBFD`.
- Sidebar/header/card surface: `#FFFFFF`.
- Divider and control border: `#DCEAF5`.

Desktop app shell structure:

```txt
sidebar 260px
main
  header 72px
  scrollable content
```

Focused flow pages may use a smaller `56px` sticky header and a `720px` to `760px` content max width.

## Language Switch Standard

App shell pages must use a segmented `TH / EN` control.

Standard app shell language switch:

- Labels: `TH` and `EN`.
- Height: `36px`.
- Outer radius: `12px`.
- Active button radius: `9px`.
- Active state: navy background and white text.
- Inactive state: white or muted background with secondary text.
- State key: `performia_demo_lang`.

Use only `performia_demo_lang` for persisted language state.

The login shell may keep its floating language switch.

The assessment focused flow uses the same segmented `TH / EN` language control in its compact focused header. It must store language in `performia_demo_lang`.

## Profile Menu Standard

The header avatar opens the profile menu on app shell pages.

Menu items:

- Profile
- Settings
- Switch Account

Switch Account behavior:

```js
localStorage.removeItem("performia_demo_role");
window.location.href = "/login.html";
```

Standard menu styling:

- Width: `188px`.
- Radius: `12px`.
- Padding: `6px`.
- Item height: `36px`.
- Item radius: `9px`.
- Surface: white.
- Border: `#DCEAF5`.
- Shadow: `0 12px 32px rgba(6,24,73,0.14)`.

If a sidebar user block is clickable, it should either open the same profile menu or be made visually static. Avoid mixing static avatars and menu avatars in a way that makes similar controls behave differently.

## Navigation Standards

### Employee Navigation Order

Use this order for employee app shell navigation:

1. Home
2. Assessment
3. PERFORM-6 Profile
4. Activities
5. Credit Wallet
6. My Bookings
7. Feedback
8. Help Center

Root-relative routes:

```txt
/employee/
/employee/assessment.html
/employee/
/employee/marketplace.html
/employee/marketplace.html
/employee/marketplace.html
/employee/
/employee/
```

### HR Navigation Behavior

HR navigation may be generated from JavaScript, but it should remain within the HR portal and keep active state local to `/hr/dashboard.html` unless more HR pages are added.

HR nav may include section labels and badges when useful for dashboard scanning.

### Active and Hover Styles

Standard app shell nav item:

- Height: `44px`.
- Radius: `14px`.
- Padding: `0 14px`.
- Text size: `14px`.
- Text weight: `500`.
- Icon size: `18px` to `20px`.
- Default text: `#52627A`.
- Hover background: `#F3F7FA`.
- Hover text: `#071B63`.
- Active background: `#EEF8FF`.
- Active text: `#071B63`.
- Active icon: `#10D5D2`.
- Active indicator: `3px` aqua left bar.

## Button Standards

### Primary Button

- Height: `44px`.
- Radius: `14px`.
- Padding: `0 20px`.
- Background: `#071B63`.
- Text: white.
- Font size: `14px`.
- Font weight: `600`.
- Hover background: `#031244`.

### Secondary Button

- Height: `44px`.
- Radius: `14px`.
- Padding: `0 20px`.
- Background: white.
- Text: `#071B63`.
- Border: `1px solid #DCEAF5`.
- Font size: `14px`.
- Font weight: `600`.
- Hover background: `#EEF8FF`.

### Ghost Button

- Height: `40px` to `44px`.
- Radius: `12px` to `14px`.
- Background: transparent.
- Text: `#52627A`.
- Hover background: `#EEF8FF`.
- Hover text: `#071B63`.

### Small Button

- Height: `36px`.
- Radius: `10px` to `12px`.
- Font size: `12px` to `13px`.
- Font weight: `600`.

Gradient buttons are reserved for the login shell. App shell buttons should use flat navy/white styles.

## Card Standards

### Default App Card

- Background: white.
- Border: `1px solid #DCEAF5`.
- Radius: `24px`.
- Padding: `24px`.
- Optional shadow: `0 1px 8px rgba(6,24,73,0.06)`.
- Optional hover shadow: `0 4px 24px rgba(6,24,73,0.10)`.

### Compact Card

Use in focused flow pages and dense control surfaces:

- Radius: `16px`.
- Padding: `16px` to `20px`.
- Border: `1px solid #DCEAF5`.

### Activity Card

Use marketplace card behavior as the canonical activity card standard:

- Radius: `24px`.
- Image height: `160px`.
- Body padding: `16px`.
- Border: `1px solid #DCEAF5`.
- Hover: slight elevation and optional `translateY(-2px)` to `translateY(-3px)`.
- Badges may overlay the image with translucent navy or light surfaces.

Avoid creating visually incompatible activity cards in assessment recommendations or employee home recommendations. If a compact variant is needed, document it as a variant of the same activity card.

## Spacing Standards

Use this spacing scale for new UI changes:

- `4px`: tight icon/text gaps.
- `6px`: compact inline gaps.
- `8px`: standard small gap.
- `10px`: compact control gap.
- `12px`: standard control gap.
- `16px`: compact card padding and mobile spacing.
- `20px`: section internals and grid gaps.
- `24px`: default card padding and section gaps.
- `28px`: large card/hero internal gap.
- `32px`: desktop page padding.
- `40px`: large hero or login shell spacing.

Recommended defaults:

- Desktop page padding: `32px`.
- Mobile page padding: `16px` to `20px`.
- Card padding: `24px`.
- Grid gap: `20px` to `24px`.
- Header control gap: `10px` to `12px`.
- Focused flow content padding: `20px`.

## Interaction Rules

- If an element looks clickable, it must have a working click behavior or be styled as static.
- Header avatars on app shell pages should open the profile menu.
- Switch Account must clear `performia_demo_role` and redirect to `/login.html`.
- Language persistence must use `performia_demo_lang`.
- Do not add real authentication.
- Do not add database or backend integration.
- Do not fetch remote APIs for UI state.
- Use root-relative internal links.
- Do not link to original source filenames.
- Preserve the current visual language when making incremental UI changes.
- Before changing runtime UI, compare the target page against this document and keep shell-specific exceptions explicit.

# Shell Consistency Priority

When a page belongs to App Shell:

1. Follow `employee/marketplace.html`.
2. Follow `docs/UI_STANDARDS.md`.
3. Preserve page-specific content.

When a page belongs to Login Shell or Focused Flow Shell:

Do not normalize it into App Shell.
