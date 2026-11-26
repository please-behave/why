# Visual identity

[DEC-0009](../why/decisions/DEC-0009.yaml) establishes the shared visual identity. Components use the semantic token names below in both themes. Hex values are sRGB.

## Logo

- Use [logo.svg](logo.svg) on light surfaces. Use [logo-dark.svg](logo-dark.svg) on dark surfaces, where its off-white outline preserves the shield silhouette.
- Keep clear space of at least one eighth of the visible mark’s height on all sides, measured from the outer edge, including the outline when present.
- Render the SVG at a minimum height of 32 CSS pixels and preserve its aspect ratio.

## Brand tokens

The values are the most frequent RGB samples in flat interior patches of the original raster’s indigo, coral and off-white shapes. The logo uses the same fills in both themes.

| Token | Role | Light and dark |
|---|---|---|
| `brand-primary` | Indigo | `#251257` |
| `brand-accent` | Coral | `#FE603F` |
| `brand-light` | Off-white | `#FDFAFA` |

## Neutral tokens

| Token | Role | Light | Dark |
|---|---|---|---|
| `surface` | Page background | `#FFFFFF` | `#15131C` |
| `surface-raised` | Panel background | `#F5F4F7` | `#23202C` |
| `border` | Meaningful control boundaries and dividers | `#77717F` | `#888291` |
| `text-muted` | Secondary text | `#605B69` | `#B1AAB9` |
| `text` | Primary text | `#201D27` | `#F7F5F9` |

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

| Foreground | Light on `surface` | Light on `surface-raised` | Dark on `surface` | Dark on `surface-raised` |
|---|---:|---:|---:|---:|
| `text` | 16.58:1 | 15.13:1 | 16.98:1 | 14.75:1 |
| `text-muted` | 6.57:1 | 5.99:1 | 8.16:1 | 7.09:1 |
| `border` | 4.72:1 | 4.30:1 | 4.95:1 | 4.30:1 |
| `status-passed` | 7.01:1 | 6.40:1 | 10.41:1 | 9.04:1 |
| `status-failed` | 7.55:1 | 6.89:1 | 8.62:1 | 7.49:1 |
| `status-error` | 7.86:1 | 7.18:1 | 10.06:1 | 8.74:1 |
| `status-warning` | 7.55:1 | 6.89:1 | 10.61:1 | 9.22:1 |
| `status-not-run` | same as `text-muted` | same as `text-muted` | same as `text-muted` | same as `text-muted` |
| `status-allowed` | 6.75:1 | 6.16:1 | 12.39:1 | 10.76:1 |

For Rule Set chips, compute WCAG relative luminance from the sRGB values and divide the lighter luminance plus 0.05 by the darker luminance plus 0.05. The unrounded ratios meet 4.5:1 for the label on the chip fill and 3:1 for the outline against the fill and both surrounding surfaces.

| Foreground | Background | Light | Dark |
|---|---|---:|---:|
| `rule-set-text` | `rule-set-surface` | 7.75:1 | 8.09:1 |
| `rule-set` | `rule-set-surface` | 3.77:1 | 4.70:1 |
| `rule-set` | `surface` | 4.44:1 | 7.35:1 |
| `rule-set` | `surface-raised` | 4.05:1 | 6.39:1 |

Use `brand-primary` text on `brand-accent` and `brand-light` text on `brand-primary` for branded surfaces in either theme.

| Foreground | Background | Ratio |
|---|---|---:|
| `brand-primary` | `brand-accent` | 5.34:1 |
| `brand-light` | `brand-primary` | 15.53:1 |
| White (`surface` in light mode) | `brand-accent` | 3.02:1, below AA for normal text |
| `brand-light` | `brand-accent` | 2.91:1, below AA for text |
| `brand-light` outline | `surface` in dark mode | 17.72:1 |
| `brand-light` outline | `surface-raised` in dark mode | 15.39:1 |
