# Interface palette

The [shared visual identity decision](../why/decisions/DEC-0028.yaml) establishes this palette for Please Behave interfaces. Use semantic token names in both themes. Hex values are sRGB and aliases use the named token in the same theme. The [visual identity document](README.md) defines the logo and its brand tokens.

## Neutral tokens

| Token | Role | Light | Dark |
|---|---|---|---|
| `surface` | Page background | `#FFFFFF` | `#15131C` |
| `surface-raised` | Panel background | `#F4F7FB` | `#202734` |
| `border` | Component-identifying boundaries for inputs, buttons, badges and chips | `#77717F` | `#888291` |
| `border-subtle` | Decorative table row separators, section rules and dividers within widgets | `#BCC8D8` | `#46556A` |
| `text-muted` | Secondary text | `#605B69` | `#B1AAB9` |
| `text` | Primary text | `#201D27` | `#FFFFFF` |

Both themes tint `surface-raised` and `border-subtle` slightly blue. The tint connects panels and dividers to the interactive blue while keeping the stronger accents for controls. White serves as the light page surface and the dark primary text color.

Use `border-subtle` only where the content stays perceivable without the divider. Use `border` wherever an outline is the sole cue that identifies a component.

## Interface blue tokens

| Token | Role | Light | Dark |
|---|---|---|---|
| `accent-link` | Links and interactive text | `#1459C7` | `#8AB8FF` |
| `accent-link-hover` | Hovered links and interactive text | `#103F98` | `#B7D4FF` |
| `accent-focus` | Keyboard focus ring | `#2563EB` | `#7BAAFF` |
| `accent-fill` | Primary action fill | `#1C56BD` | `accent-link` |
| `accent-text` | Label on a primary action fill | `surface` | `surface` |
| `accent-surface` | Tinted background for selected rows and interactive panels | `#EAF2FF` | `#243653` |
| `nav-hover-surface` | Background for hovered navigation segments | `accent-surface` | `#10121B` |

Use lighter blue steps in the dark theme for links, focus and action fills. Underline content links. Use a visible label, indicator or boundary when the tinted background conveys a state. Separate a focus ring from a filled control with a gap that shows the surrounding surface.

## Badge tones

Use a tint, label and outline for each classification. Plain badges use `accent-surface`, `text` and `border`. Keep the visible classification label in every theme.

| Token | Role | Light | Dark |
|---|---|---|---|
| `chip-check-surface` | Check surface | `#DCF3F0` | `#12312F` |
| `chip-check-text` | Check text | `#0A4A45` | `#A4E6DD` |
| `chip-check-border` | Check border | `#2A7F78` | `#4DA89E` |
| `chip-review-surface` | Review surface | `#E3EDFC` | `accent-surface` |
| `chip-review-text` | Review text | `#173F80` | `accent-link-hover` |
| `chip-review-border` | Review border | `#3565AD` | `accent-focus` |
| `chip-blocking-surface` | Blocking surface | `#C5CDD8` | `#475268` |
| `chip-blocking-text` | Blocking text | `#0F1623` | `#F4F7FB` |
| `chip-blocking-border` | Blocking border | `#3A485C` | `#B4C0D4` |
| `chip-neutral-surface` | Non-blocking surface | `#EEEEF0` | `#2C2B32` |
| `chip-neutral-text` | Non-blocking text | `#3A3A42` | `#D0CED8` |
| `chip-neutral-border` | Non-blocking border | `#7A7A85` | `#8F8C99` |

## Status tokens

Apply status tokens to labels and symbols on neutral surfaces. A status indicator in an interactive tile or chip retains its color when the surface changes on hover.

| Token | Meaning | Light | Dark |
|---|---|---|---|
| `status-passed` | Passed (green), or current repository evidence | `#176639` | `#78D69A` |
| `status-failed` | Failed (red), or a repository that has never integrated | `#A41C2C` | `#FF929C` |
| `status-error` | Verification error | `#753396` | `#DAB0F3` |
| `status-warning` | Warning, including overdue repository evidence | `#884000` | `#F5B97C` |
| `status-not-run` | Not run, or unknown repository status | `text-muted` | `text-muted` |
| `status-allowed` | Not yet satisfied but allowed (yellow), including repository evidence pending within its grace period | `#725800` | `#F3D16B` |

## Rule Set token

Use the muted platinum blue `rule-set` token to identify shared Rule Sets. Bundles of local rules use neutral tokens only. For a filled chip, use `rule-set` for the outline and pair it with the matching surface and label text.

| Token | Role | Light | Dark |
|---|---|---|---|
| `rule-set` | Chip outline | `#637A92` | `#91A6BD` |
| `rule-set-surface` | Chip fill | `#E7EDF4` | `#2B3949` |
| `rule-set-text` | Chip label | `#344A61` | `#C8D8E7` |

## Verified contrast

Use at least 4.5:1 for normal text and 3:1 for large text, meaningful interface components and graphics under WCAG 2.2 AA. Large text is at least 18 pt regular or 14 pt bold. The ratios below use WCAG relative luminance with unrounded values checked against the thresholds. [Text contrast](https://www.w3.org/TR/WCAG22/#contrast-minimum) · [Non-text contrast](https://www.w3.org/TR/WCAG22/#non-text-contrast)

### Page and raised surfaces

Decorative `border-subtle` dividers carry no information on their own and have no minimum contrast requirement. Status indicators use the neutral surfaces.

| Foreground | Light on `surface` | Light on `surface-raised` | Dark on `surface` | Dark on `surface-raised` |
|---|---:|---:|---:|---:|
| `text` | 16.58:1 | 15.43:1 | 18.39:1 | 14.99:1 |
| `text-muted` | 6.57:1 | 6.11:1 | 8.16:1 | 6.65:1 |
| `border` | 4.72:1 | 4.39:1 | 4.95:1 | 4.03:1 |
| `border-subtle` | 1.69:1 | 1.58:1 | 2.42:1 | 1.98:1 |
| `accent-link` | 6.40:1 | 5.95:1 | 9.09:1 | 7.41:1 |
| `accent-link-hover` | 9.60:1 | 8.94:1 | 12.15:1 | 9.90:1 |
| `accent-focus` | 5.17:1 | 4.81:1 | 7.91:1 | 6.45:1 |
| `accent-fill` | 6.74:1 | 6.27:1 | 9.09:1 | 7.41:1 |
| `status-passed` | 7.01:1 | 6.52:1 | 10.41:1 | 8.48:1 |
| `status-failed` | 7.55:1 | 7.03:1 | 8.62:1 | 7.03:1 |
| `status-error` | 7.86:1 | 7.32:1 | 10.06:1 | 8.20:1 |
| `status-warning` | 7.55:1 | 7.03:1 | 10.61:1 | 8.64:1 |
| `status-not-run` | 6.57:1 | 6.11:1 | 8.16:1 | 6.65:1 |
| `status-allowed` | 6.75:1 | 6.28:1 | 12.39:1 | 10.09:1 |

### Blue surfaces

A primary action's fill identifies the control against its surroundings. Its label uses `accent-text`. A meaningful boundary on a tinted background uses `border`.

| Foreground | Background | Light | Dark |
|---|---|---:|---:|
| `accent-text` | `accent-fill` | 6.74:1 | 9.09:1 |
| `text` | `accent-surface` | 14.72:1 | 12.16:1 |
| `text-muted` | `accent-surface` | 5.83:1 | 5.39:1 |
| `accent-link` | `accent-surface` | 5.68:1 | 6.01:1 |
| `accent-link-hover` | `accent-surface` | 8.53:1 | 8.03:1 |
| `border` | `accent-surface` | 4.19:1 | 3.27:1 |
| `accent-focus` | `accent-surface` | 4.59:1 | 5.23:1 |
| `accent-fill` | `accent-surface` | 5.98:1 | 6.01:1 |
| `status-passed` | `accent-surface` | 6.22:1 | 6.88:1 |
| `status-failed` | `accent-surface` | 6.70:1 | 5.70:1 |
| `status-error` | `accent-surface` | 6.98:1 | 6.65:1 |
| `status-warning` | `accent-surface` | 6.71:1 | 7.01:1 |
| `status-not-run` | `accent-surface` | 5.83:1 | 5.39:1 |
| `status-allowed` | `accent-surface` | 5.99:1 | 8.19:1 |

### Hovered navigation

The hover outline and inset focus ring remain visible against the hover surface.

| Foreground | Background | Light | Dark |
|---|---|---:|---:|
| `accent-link-hover` | `nav-hover-surface` | 8.53:1 | 12.34:1 |
| `border` | `nav-hover-surface` | 4.19:1 | 5.02:1 |
| `accent-focus` | `nav-hover-surface` | 4.59:1 | 8.04:1 |

### Classification badges

Text contrasts with the tint and surrounding neutral surfaces. The outline identifies the badge against both its tint and its surroundings.

| Foreground | Light on tint | Dark on tint | Light on page | Dark on page | Light on raised | Dark on raised |
|---|---:|---:|---:|---:|---:|---:|
| `chip-check-text` | 8.72:1 | 9.92:1 | 10.10:1 | 13.09:1 | 9.40:1 | 10.66:1 |
| `chip-check-border` | 4.11:1 | 4.92:1 | 4.77:1 | 6.49:1 | 4.44:1 | 5.29:1 |
| `chip-review-text` | 8.64:1 | 8.03:1 | 10.20:1 | 12.15:1 | 9.49:1 | 9.90:1 |
| `chip-review-border` | 4.92:1 | 5.23:1 | 5.81:1 | 7.91:1 | 5.40:1 | 6.45:1 |
| `chip-blocking-text` | 11.30:1 | 7.31:1 | 18.11:1 | 17.12:1 | 16.86:1 | 13.95:1 |
| `chip-blocking-border` | 5.79:1 | 4.27:1 | 9.29:1 | 10.01:1 | 8.64:1 | 8.16:1 |
| `chip-neutral-text` | 9.72:1 | 9.01:1 | 11.27:1 | 11.83:1 | 10.49:1 | 9.64:1 |
| `chip-neutral-border` | 3.66:1 | 4.26:1 | 4.24:1 | 5.59:1 | 3.95:1 | 4.55:1 |

### Rule Set chips

The outline contrasts with the chip fill and with the surrounding neutral surface.

| Foreground | Background | Light | Dark |
|---|---|---:|---:|
| `rule-set-text` | `rule-set-surface` | 7.75:1 | 8.09:1 |
| `rule-set` | `rule-set-surface` | 3.77:1 | 4.70:1 |
| `rule-set` | `surface` | 4.44:1 | 7.35:1 |
| `rule-set` | `surface-raised` | 4.13:1 | 5.99:1 |

### Identity surfaces

Use the verified text pairings on [identity surfaces](README.md#brand-tokens). The logo's light outline contrasts with both dark neutral surfaces.

| Foreground | Background | Ratio |
|---|---|---:|
| `brand-primary` | `brand-accent` | 5.34:1 |
| `brand-light` | `brand-primary` | 15.53:1 |
| `surface` (light theme) | `brand-accent` | 3.02:1 (below AA for normal text) |
| `brand-light` | `brand-accent` | 2.91:1 (below AA for text) |
| `brand-light` outline | `surface` (dark theme) | 17.72:1 |
| `brand-light` outline | `surface-raised` (dark theme) | 14.44:1 |
