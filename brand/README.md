# Visual identity

[DEC-0028](../why/decisions/DEC-0028.yaml) establishes the shared visual identity. Use the [interface palette](palette.md) for interface text, links, headings and controls.

The [interface principles](interface-principles.md) govern how web views use this identity.

## Logo

- Use [logo.svg](logo.svg) on light surfaces. Use [logo-dark.svg](logo-dark.svg) on dark surfaces, where its off-white outline preserves the shield silhouette.
- Keep clear space of at least one eighth of the visible mark’s height on all sides, measured from the outer edge, including the outline when present.
- Render the SVG at a minimum height of 32 CSS pixels and preserve its aspect ratio.

## Brand tokens

The values are the most frequent RGB samples in flat interior patches of the original raster’s indigo, coral and off-white shapes. The logo uses the same fills in both themes. Brand tokens are reserved for the logo and identity surfaces.

| Token | Role | Light and dark |
|---|---|---|
| `brand-primary` | Indigo | `#251257` |
| `brand-accent` | Coral | `#FE603F` |
| `brand-light` | Off-white | `#FDFAFA` |
