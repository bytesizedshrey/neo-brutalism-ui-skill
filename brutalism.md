---
name: neo-brutalism-ui
description: Build neo-brutalism UI components (cards, buttons, inputs, badges, navbars, modals) with hard offset shadows, thick black borders, flat vivid surfaces, and translate-on-press interaction patterns. Trigger this skill when the user asks for brutalist components, neo-brutal design, hard-shadow cards, chunky UI, or bold flat web interfaces.
---

# Neo-Brutalism UI

Use this skill to design and implement neo-brutalism components with consistent hard shadows, chunky borders, flat vivid color, and snappy press interactions.

## Non-Negotiable Foundations

- Page background must use a warm neutral in the `#e3dfd7` to `#f5f1eb` range, or the grid-overlay pattern.
- Every container and interactive element must have a **solid black border** of `border-2` (`2px`).
- Shadows are always **hard offset** — zero blur, solid black. This is the defining mark of the style.
- Shadow direction is always **bottom-right** (`+x, +y`). Consistent across every element on the page.
- No gradients on surfaces. Flat color only. Period.
- Every interactive element must **translate toward its shadow and collapse the shadow** on hover/active.

## Core Material Recipes

### 1) Hard-Shadow Card (main container body)

Use for the primary content housing — cards, panels, dialogs, sections.

- Base:
  - `bg-main` (a vivid flat accent — see Color Palette below)
- Border + shadow recipe:
  - `border-2 border-border rounded-base shadow-shadow`
- `shadow-shadow` resolves to:
  - `shadow-[4px_4px_0px_0px_#000000]`
- Hover interaction (translate + collapse):
  - `hover:translate-x-boxShadowX hover:translate-y-boxShadowY hover:shadow-none`
  - `boxShadowX` / `boxShadowY` resolve to `4px` each (matching the shadow offset)

Notes:
- The shadow is a solid black rectangle offset bottom-right. No blur, no spread beyond offset.
- On hover, the card translates `+4px, +4px` and the shadow disappears — creating a "pressed flat" feel.
- `rounded-base` resolves to a small radius (`5px`). Never use `rounded-full` on containers.

### 2) Secondary Surface (input wells, content backgrounds, secondary panels)

Use for input fields, dropdown backgrounds, secondary card interiors, form zones.

- Base color:
  - `bg-secondary-background` (a lighter neutral — `#e3dfd7` in light mode)
- Border:
  - `border-2 border-border`
- Corner:
  - `rounded-base`
- No shadow on secondary surfaces — they sit flush inside a parent card.

Notes:
- Secondary surfaces are visually recessed by contrast alone. They are lighter/neutral against a vivid parent.
- They never carry their own hard shadow. The parent card owns the shadow.

### 3) Elevated Interactive Object (buttons, nav items, action controls)

Use for all clickable elements — buttons, icon actions, nav links with shadow.

- Primary button:
  - `bg-main text-main-foreground border-2 border-border shadow-shadow rounded-base`
- Secondary / neutral button:
  - `bg-secondary-background text-foreground border-2 border-border shadow-shadow rounded-base`
- Hover state (mandatory — the signature interaction):
  - `hover:translate-x-boxShadowX hover:translate-y-boxShadowY hover:shadow-none`
  - Transition: `transition-all` (keep it snappy, no duration override needed)
- Nav-specific shadow variant:
  - `shadow-nav` → `shadow-[4px_4px_0px_0px_#000000]` (same value, aliased for semantic clarity)

Notes:
- Translation direction MUST match shadow direction. Shadow is bottom-right, so translate is `+x, +y`.
- The translation distance equals the shadow offset. `4px` shadow → `4px` translate.
- After translate, shadow is `none` — the element appears pressed flat against the surface.

## Component Architecture Pattern

When building a neo-brutalism page, structure in this order:

1. Page background (warm neutral or grid-overlay pattern)
2. Navbar with bottom border (`border-b-4 border-border`)
3. Parent hard-shadow cards (`bg-main` + `shadow-shadow`)
4. Secondary surfaces inside cards (`bg-secondary-background`, no shadow)
5. Elevated interactive objects (buttons with `shadow-shadow` + translate-on-hover)
6. Decorative accents (badges, rotated stickers, grid patterns)

This layer order is mandatory for the flat-but-tactile depth hierarchy.

## Interaction Rules

- **Press-flat is non-negotiable.** Every clickable element with a shadow must:
  - Translate toward the shadow direction on hover
  - Collapse the shadow to `none`
  - Use `transition-all` for the motion
- **No elastic/bouncy easing.** The transition should feel mechanical and instant.
- **Focus states must be bold:**
  - `focus-visible:ring-2 focus-visible:ring-black focus-visible:ring-offset-2`
  - Never use a thin, subtle outline. The ring must be clearly visible.
- **Disabled states:**
  - `disabled:pointer-events-none disabled:opacity-50`
  - Shadow may remain but element is visually muted.
- **Cursor rules:**
  - `cursor-pointer` on all interactive elements.
  - `disabled:cursor-not-allowed` on disabled states.

## Button Guidance

- Use `h-10 px-4 py-2` for standard size.
- Text: `text-sm font-base` (the library uses `font-base` for body, `font-heading` for labels/titles).
- Icon buttons: `size-9 p-0` with `[&_svg]:size-4`.
- Variant hierarchy:
  - **Default (accent):** `bg-main text-main-foreground`
  - **Secondary:** `bg-secondary-background text-foreground`
  - **Neutral (outline-like):** `bg-secondary-background text-foreground` with identical border + shadow.
- All variants share: `border-2 border-border shadow-shadow hover:translate-x-boxShadowX hover:translate-y-boxShadowY hover:shadow-none`.

## Color and Accent Rules

- Accent color (`bg-main`) can vary by project, but the structural tokens stay fixed:
  - Borders are always `border-border` (solid black in light mode).
  - Shadows are always `shadow-shadow` (solid black offset).
  - Text on accent surfaces: `text-main-foreground` (black).
  - Text on neutral surfaces: `text-foreground` (black).
- **Never use white text.** Neo-brutalism keeps text black on all surfaces because accent colors are chosen to be high-contrast readable with black.
- Accent glow / color should support hierarchy, not noise. One accent per card.

### Default Color Palette

Use as CSS custom properties via Tailwind theme:

| Token                  | Light Mode Value         | Purpose                          |
|------------------------|--------------------------|----------------------------------|
| `--background`         | `#e3dfd7`                | Page background                  |
| `--foreground`         | `#000000`                | Primary text                     |
| `--main`               | `#88aaee`                | Accent / primary surface         |
| `--main-foreground`    | `#000000`                | Text on accent surfaces          |
| `--secondary-background` | `#e3dfd7`              | Input wells, secondary panels    |
| `--border`             | `#000000`                | All borders                      |
| `--ring`               | `#000000`                | Focus rings                      |

### Vivid Accent Alternatives (swap into `--main`)

- Blue: `#88aaee`
- Yellow: `#FFD166`
- Coral: `#FF6B6B`
- Cyan: `#A6FAFF`
- Mint: `#B8F2E6`
- Lavender: `#C3B1E1`
- Lime: `#c4e54d`
- Peach: `#FFBF69`

## Reusable Tailwind Tokens

Use these as defaults unless user asks otherwise:

- Page bg: `bg-[#e3dfd7]`
- Page bg (grid pattern variant):
  - `bg-[#e3dfd7] bg-[linear-gradient(to_right,#80808033_1px,transparent_1px),linear-gradient(to_bottom,#80808033_1px,transparent_1px)] bg-[size:70px_70px]`
- Hard-shadow card:
  - `bg-[#88aaee] border-2 border-black rounded-[5px] shadow-[4px_4px_0px_0px_#000000]`
- Hard-shadow card (hover interaction):
  - `hover:translate-x-[4px] hover:translate-y-[4px] hover:shadow-none transition-all`
- Secondary surface (input/panel interior):
  - `bg-[#e3dfd7] border-2 border-black rounded-[5px]`
- Primary button:
  - `bg-[#88aaee] text-black border-2 border-black rounded-[5px] shadow-[4px_4px_0px_0px_#000000] hover:translate-x-[4px] hover:translate-y-[4px] hover:shadow-none transition-all h-10 px-4 py-2 text-sm font-semibold`
- Secondary button:
  - `bg-[#e3dfd7] text-black border-2 border-black rounded-[5px] shadow-[4px_4px_0px_0px_#000000] hover:translate-x-[4px] hover:translate-y-[4px] hover:shadow-none transition-all h-10 px-4 py-2 text-sm font-semibold`
- Text input:
  - `bg-[#e3dfd7] border-2 border-black rounded-[5px] h-10 px-3 py-2 text-sm focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-black focus-visible:ring-offset-2`
- Navbar:
  - `border-b-4 border-black bg-[#e3dfd7]`
- Hard shadow (default):
  - `shadow-[4px_4px_0px_0px_#000000]`
- Hard shadow (nav — identical value, semantic alias):
  - `shadow-[4px_4px_0px_0px_#000000]`

## Typography and Density (Compact Default)

- Default to compact, UI-realistic scale. Do not oversize text.
- Use two font families:
  - `font-heading`: A bold/black weight sans-serif (`Lexend`, `Space Grotesk`, or project default). Used for labels, titles, card headers.
  - `font-base`: A medium-weight readable sans-serif (`Lexend`, `Inter`, or project default). Used for body text, descriptions, button labels.
- Unless the user asks for a hero layout, keep component height and type dense:
  - Card titles: `text-base font-heading leading-none`
  - Card descriptions: `text-sm font-base`
  - Button text: `text-sm font-base`
  - Input text: `text-sm font-base`
  - Labels: `text-sm font-heading leading-none`
- Keep vertical rhythm tight: prefer smaller paddings/gaps before increasing font size.
- Scale icons with text hierarchy: `[&_svg]:size-4` for standard, `[&_svg]:size-5` for nav.

## Quality Checklist (must pass)

- Background is warm neutral (`#e3dfd7` to `#f5f1eb`) or uses the grid-overlay pattern.
- Every container has `border-2 border-black` (or `border-border`).
- Every shadow is hard offset, zero blur: `shadow-[4px_4px_0px_0px_#000000]`.
- Shadow direction is consistently bottom-right across all elements.
- Every interactive element with a shadow translates on hover and collapses the shadow.
- Translation distance matches shadow offset (`4px` shadow → `4px` translate).
- No gradients on any surface. Flat color only.
- Typography uses `font-heading` for titles/labels, `font-base` for body. No thin/light weights.
- Text is always black — no white text on any surface.
- Focus states use `ring-2 ring-black ring-offset-2` — clearly visible.
- `rounded-base` (`5px`) on all containers. No `rounded-full` on cards or panels.
- Accent color supports hierarchy, not noise. One vivid accent per card.

## Anti-Patterns

- Blurred shadows anywhere. Zero blur is the entire identity.
- Thin (`1px`) or missing borders. Must be `border-2` minimum.
- Gradient fills on cards or buttons.
- Elastic / bouncy / spring animations. Keep it mechanical.
- `rounded-full` on rectangular containers or cards.
- Shadow that does not collapse on hover/active. The press-flat is the whole point.
- Inconsistent shadow direction (some bottom-right, some bottom-left). Pick one, stick with it.
- White or light-colored text. Always black.
- Opacity/transparency on borders. Borders are solid black.
- Secondary surfaces carrying their own hard shadow. Only parent cards and buttons own shadows.
- Background lighter than the card surface (inverts the hierarchy).

## If User Provides Existing Brutalist Code

- Preserve the existing border weight and shadow offset first.
- Adjust only tokens needed for consistency with this system.
- Do not replace hand-tuned shadow offsets with generic presets if the originals are intentional.
- Match the existing shadow direction across new elements you add.

## Dark Mode Variant

When the user requests dark neo-brutalism:

- Page background: swap to `#1a1a1a` to `#272733`
- Card surface: `bg-main` stays vivid (same accent palette) or use `bg-[#272733]`
- Border color: swap to `border-[#000000]` (stays black) or `border-white` if going full inverted
- Shadow color: `shadow-[4px_4px_0px_0px_#000000]` (black on dark bg is valid and canonical) or invert to `shadow-[4px_4px_0px_0px_#ffffff]`
- Text: `text-white` on dark surfaces, `text-black` on vivid accent surfaces
- Same press physics, same border weights, same translate-on-hover rules — only colors invert.

## Nested Card + Button Pattern (Learned Rule)

- When a card contains multiple action buttons, each button is an **independent elevated object** with its own shadow.
- Correct structure:
  - `Card (hard-shadow)` → `Content area` → `Button (own shadow + own translate-on-hover)`
- Buttons inside cards use `w-full` to fill the card's content width.
- Stack buttons with `flex-col gap-2` inside the card footer.
- Avoid:
  - Grouping multiple buttons under a single shared shadow.
  - Buttons without their own border + shadow when placed inside a card.

## Surface Material Consistency (Learned Rule)

- All cards and containers at the same hierarchy level should use the **same accent surface color** (`bg-main`) by default.
- Do not introduce a different accent for each card unless the user explicitly asks for color variety.
- Secondary surfaces (`bg-secondary-background`) are reserved for **input wells and recessed areas inside cards**, not for standalone containers.
- Default accent to reuse:
  - `bg-[#88aaee]` (or whichever value is set as `--main`)
