# Bloom — Psychology with Hannah (v2 — Cinematic Edition)

A static, production-ready marketing site for Bloom, a wellness-integrated mental health practice. Built with semantic HTML5 and Tailwind CSS (via CDN), no build step required. Fully responsive from ~360px phones up through desktop.

## What changed in this update

1. **Cinematic visual system** — every page now uses layered gradient "scenes" (`.scene-light` / `.scene-dark`), soft blurred glow blobs in clay/sage tones, a subtle full-page film-grain texture, and a hospitality-style **arch frame** component (the rounded doorway shape used in boutique hotel/spa branding) to present artwork. Random stock photography from the web was deliberately avoided — those images aren't licensed for redistribution on your own GitHub Pages site — and the "cinematic hotel" mood was built instead from original gradients, texture, and your own brand assets. If you'd like real photography (headshots, office/room photos), drop the files into `/images` and swap them into the `arch-frame__inner` containers.
2. **Real images embedded from your PDFs** — extracted directly from the two brand documents and placed into `/images`:
   - `bloom-logo.png` — the Bloom wordmark, background-removed, used in the nav and footer of every page (blends automatically onto both light and dark sections)
   - `mind-body-spirit.jpg` — the concentric-rings diagram, featured on the Home and Approach pages
   - `wellness-journey.jpg` — the "Wellness is a Journey" graphic, featured on the Journey page
   - `holistic-health.jpg` — the "Holistic Health Is / Isn't" comparison graphic, featured on the Services page
3. **Mobile overlap fixes** — rebuilt spacing, type scale, and grid breakpoints across every section (added an `xs: 440px` Tailwind breakpoint for small phones). Nav height, hero padding, accordion indentation, button widths, and image frames were all specifically re-tuned so nothing overlaps or overflows between ~360px and desktop. `overflow-x: hidden` is set at the body level as a safety net.
4. **More content from the frameworks** — the Approach, Services, Journey and About pages now carry closer to the full text of both PDFs (session structure, scope & ethics, indicators of progress, who Bloom supports, tone-of-voice word lists, etc.), not just the summarized version from the first draft.

## File structure

```
bloom-site/
├── index.html         Home — cinematic hero, brand pillars, MBS teaser (real artwork), journey teaser, CTA
├── approach.html       Approach — real MBS artwork + tabbed captions, positioning, personality, tone of voice
├── services.html       Services — clinical services, real Holistic Health artwork, session structure, ethics
├── journey.html         The Journey — real Wellness-Journey artwork, 5-stage accordion, progress indicators
├── about.html            About — practitioner bio (placeholder), who we support, ethical commitment
├── contact.html          Contact — soft inquiry form, safety note
├── images/
│   ├── bloom-logo.png        Extracted & background-removed logo
│   ├── mind-body-spirit.jpg  Extracted MBS rings diagram
│   ├── wellness-journey.jpg  Extracted wellness journey diagram
│   └── holistic-health.jpg   Extracted holistic health comparison
├── css/style.css        Fonts, tokens, cinematic scenes, arch frames, grain texture, mobile rules
├── js/tailwind-config.js  Tailwind CDN theme (colors, type, breakpoints incl. xs, motion)
└── js/main.js             Scroll reveals, mobile nav, journey accordion, MBS tab interactivity
```

## Design tokens

- **Colors:** sand `#F5F2EA` (bg), forest `#2E4635` (primary), sage `#97A98C`, clay `#B08968` (earth accent), ink `#2A2A24` (text)
- **Type:** Fraunces (display/serif, italic for signature brand lines) + Work Sans (body) + Inter (UI/utility)
- **Breakpoints:** `xs` 440px, `sm` 640px, `md` 768px, `lg` 1024px — tuned for phone-first layouts
- **Signature motifs:** concentric "bloom rings" (hero background), the arch frame (artwork presentation), flanked-hairline eyebrows (hotel-signage feel), and a soft global film-grain overlay

## Reusable components (patterns, copy-paste across pages)

- **Nav / mobile menu** — identical markup on every page; update `aria-current="page"` on the active link
- **`.scene` / `.scene-light` / `.scene-dark`** — cinematic gradient section backgrounds, pair with `.scene-vignette` and `.glow-blob` divs for depth
- **`.arch-frame` / `.arch-frame__inner`** — the hospitality-style image presentation frame; wrap any `<img>` in it
- **FeatureCard** — `article` with eyebrow label, `h3`, and paragraph, used in a `grid` with hairline gaps
- **Accordion stage** — button + `aria-expanded`/`aria-controls` panel with `max-height` transition (Journey page), driven by `js/main.js`
- **MBS tabs** — button + `data-ring` triggers swapping a caption (Approach page), same JS hook as before, now used as tabs instead of clickable SVG rings
- **CTA banner** — `.scene-dark` rounded panel with centered copy and a light button
- **Footer** — identical on every page: watermark logo, brand blurb, nav, safety note, legal line

## Before launch

1. Replace the placeholder email, phone number, and practitioner bio/photo on `about.html` and `contact.html`.
2. Wire the contact form (currently a static template) to a real booking system or email service (e.g. Formspree, a CRM, or a server-side handler).
3. If you'd like real photography instead of the gradient/arch-frame scenes, add licensed images to `/images` and swap them into the `.arch-frame__inner` `<img>` tags.
4. Add a favicon and social preview image if desired.

## Hosting on GitHub Pages

1. Push the contents of this folder to the root of your repo (or to a `/docs` folder, whichever your Pages settings point to).
2. In the repo's Settings → Pages, set the source branch/folder to match.
3. Because all paths are relative (`images/…`, `css/…`, `js/…`), it will work whether the repo is served from the root or from a `/reponame/` subpath — no path changes needed.

No build step, server, or dependencies are required.
