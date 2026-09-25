# Local Gov IMS Website — Design Refresh PR

This pull request proposes a visual and structural refresh of localgovims.digital. No content governance has been changed — this is purely a design, typography, and layout improvement.

## Summary of changes

### Why
The site is the first Google result for "Local Gov IMS" and is often the first impression councils have of the project. This PR brings it up to a standard that better reflects the quality of what the project has built.

### Design approach
- Keeps the IMS's existing teal colour as the primary hero colour on the homepage
- Introduces a warm coral/burnt orange as an alternating accent — mirroring the existing site's personality but with more polish
- Pages alternate between teal and coral headers, giving each section a distinct identity
- Typography upgraded to **Source Serif 4** (headings) and **DM Sans** (body) — readable, professional, not generic
- Warm off-white background replaces stark white — feels more approachable

---

## Files changed

### `_sass/settings/_settings.global.scss`
- Updated colour palette to teal/coral scheme
- Updated font variables to Source Serif 4 + DM Sans
- Updated `$themes` map — each page now has teal or coral as its primary header colour (alternating)

### `_sass/main.scss`
- Updated Google Fonts import for new typefaces
- Added two new component imports: `components.page-content` and `components.footer`

### `_sass/elements/_elements.page.scss`
- Warm white body background
- Updated body font, spacing, and blockquote style

### `_sass/elements/_elements.headings.scss`
- h1/h2: Source Serif 4, tighter line-height
- h3/h4: DM Sans with appropriate weights
- Subtle horizontal rules between sections

### `_sass/components/_components.navbar.scss`
- Sticky top navigation
- New brand mark (grid icon SVG)
- CTA button updated to link to tailwinddigital.io
- Mobile hamburger retained, desktop layout updated

### `_sass/components/_components.hero.scss`
- Supports eyebrow label above title
- Two modes: `max` (homepage) and `min` (inner pages)
- CTA action buttons in homepage mode
- New partner banner component below hero

### `_sass/components/_components.page-content.scss` *(new)*
- Cards, feature cards, partner cards
- Callout boxes (teal, coral, amber, green variants)
- Step-by-step component
- Provider box (dark navy, links to Tailwind Digital)
- Contact cards
- Governance holding box
- Article content styles

### `_sass/components/_components.footer.scss` *(new)*
- Navy footer, four-column grid on desktop
- Columns: brand, System, Community, Managed Service (Tailwind Digital)

---

### `_layouts/main.html`
- Added Google Fonts preconnect links
- Improved meta title format

### `_layouts/home.html`
- Full new homepage layout: partner banner, two-route getting started, feature grid preview, provider box
- No longer uses the full-width card payment image (removed)

### `_layouts/page.html`
- Uses new `c-hero.html` include with eyebrow support
- Includes new footer

### `_includes/c-navbar.html`
- New brand mark SVG
- CTA updated to "Get the IMS →" linking to tailwinddigital.io
- Active page class applied dynamically

### `_includes/c-hero.html`
- Supports `eyebrow`, `btn_primary_*`, and `btn_secondary_*` parameters

### `_includes/c-footer.html` *(new)*
- Reusable footer include used by all layouts

---

### Page markdown files
All front matter updated with `subtitle` and `eyebrow` fields for the new hero component. Content updated as follows:

| Page | Key changes |
|---|---|
| `index.markdown` | Subtitle updated; layout handles all content |
| `features/index.markdown` | Feature grid in HTML cards; open source holding note; provider box |
| `community/index.markdown` | Partner grid including Tailwind Digital; updated story; no Slack reference |
| `documentation/index.markdown` | Governance holding box; softened open source/licensing language; GitHub link with context |
| `contacts/index.markdown` | Tailwind Digital as primary contact; email as secondary; open source holding note |
| `backlog/index.markdown` | Eyebrow and subtitle added; minor copy fix ("Enanching" → "Enhancing") |

---

## Images

No new images are required — the redesign is typography and colour-led. The existing `assets/images/hero-bg.jpg` is no longer used in the homepage layout. The `card-payment.jpg` full-width image has been removed in favour of the cleaner hero approach.

If you'd like to add a hero image to the homepage in future, the `c-hero` component can accept a background image via an optional SCSS override.

---

## Testing locally

```bash
git checkout -b design-refresh
# copy these files into your local clone
bundle exec jekyll serve
# visit http://127.0.0.1:4000
```

Happy to answer any questions or make adjustments before merge.
