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

Use lighter blue steps in the dark theme for links, focus and action fills. Underline content links. Use a visible label, indicator or boundary when the tinted background conveys a state. Separate a focus ring from a filled control with a gap that shows the surrounding surface.

## Status tokens

Apply status tokens to labels and symbols on neutral surfaces.

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
