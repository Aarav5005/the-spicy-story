# FRONTEND SKILL — The Spice Story Website
> Keep this file in your project root. Reference it before building every phase.

---

## 1. Brand Tokens (copy these into your CSS :root)

```css
:root {
  /* Colors */
  --color-gold:      #d39121;  /* primary accent — CTAs, highlights, icons */
  --color-gold-dark: #b07818;  /* hover state for gold elements */
  --color-bg:        #2a2a2a;  /* main dark background */
  --color-surface:   #383632;  /* cards, nav, footer bg */
  --color-white:     #ffffff;  /* headings, primary text */
  --color-muted:     #a0a0a0;  /* secondary text, captions */
  --color-red:       #d51f0f;  /* badge accents, spice tags only */
  --color-border:    rgba(255,255,255,0.08); /* subtle dividers */

  /* Typography */
  --font-display: 'Cormorant Garamond', serif;  /* headings, hero, tagline */
  --font-body:    'Schibsted Grotesk', sans-serif; /* all body text, UI */

  /* Spacing scale */
  --space-xs:  0.5rem;
  --space-sm:  1rem;
  --space-md:  2rem;
  --space-lg:  4rem;
  --space-xl:  8rem;

  /* Border radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;

  /* Transitions */
  --transition: 0.2s ease;
}
```

---

## 2. Typography Rules

| Role | Font | Size | Weight | Color |
|------|------|------|--------|-------|
| Hero heading | Cormorant Garamond | clamp(40px, 8vw, 80px) | 400 | #ffffff |
| Section heading | Cormorant Garamond | clamp(28px, 4vw, 48px) | 400 | #ffffff |
| Tagline / italic | Cormorant Garamond | 22px | 400 italic | #d39121 |
| Body text | Schibsted Grotesk | 16px | 400 | #a0a0a0 |
| Nav links | Schibsted Grotesk | 14px | 500 | #ffffff |
| Captions / labels | Schibsted Grotesk | 12px | 400 | #a0a0a0 |
| CTA button text | Schibsted Grotesk | 14px | 600 | #1a1a1a |

Load fonts in your HTML head:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;1,400&family=Schibsted+Grotesk:wght@400;500;600&display=swap" rel="stylesheet">
```

---

## 3. Component Patterns

### CTA Button (Primary)
```css
.btn-primary {
  background: var(--color-gold);
  color: #1a1a1a;
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 600;
  padding: 12px 28px;
  border: none;
  border-radius: var(--radius-sm);
  cursor: pointer;
  letter-spacing: 0.5px;
  transition: background var(--transition);
}
.btn-primary:hover { background: var(--color-gold-dark); }
```

### CTA Button (Outline)
```css
.btn-outline {
  background: transparent;
  color: var(--color-white);
  border: 1px solid var(--color-white);
  font-family: var(--font-body);
  font-size: 14px;
  font-weight: 500;
  padding: 12px 28px;
  border-radius: var(--radius-sm);
  cursor: pointer;
  transition: all var(--transition);
}
.btn-outline:hover {
  background: var(--color-white);
  color: #1a1a1a;
}
```

### Card (Menu / Review / Experience)
```css
.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-sm) var(--space-sm);
  transition: transform var(--transition), border-color var(--transition);
}
.card:hover {
  transform: translateY(-4px);
  border-color: var(--color-gold);
}
```

### Section Wrapper
```css
.section {
  padding: var(--space-lg) var(--space-md);
  max-width: 1200px;
  margin: 0 auto;
}

/* eyebrow label above every section heading */
.eyebrow {
  font-family: var(--font-body);
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--color-gold);
  display: block;
  margin-bottom: 12px;
}
```

### Star Rating
```css
.stars { color: var(--color-gold); letter-spacing: 2px; }
.rating-count { font-size: 12px; color: var(--color-muted); margin-left: 6px; }
```

---

## 4. Grid System

```css
/* Menu cards grid */
.grid-menu {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

/* Experience 3-col */
.grid-3 {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}
@media (max-width: 768px) {
  .grid-3 { grid-template-columns: 1fr; }
}

/* Stats 4-col */
.grid-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1rem;
  text-align: center;
}
@media (max-width: 600px) {
  .grid-stats { grid-template-columns: repeat(2, 1fr); }
}
```

---

## 5. Responsive Breakpoints

```css
/* Use these ONLY — no custom pixel values */
@media (max-width: 1024px) { /* tablet */ }
@media (max-width: 768px)  { /* large mobile */ }
@media (max-width: 480px)  { /* small mobile */ }
```

---

## 6. Animation Rules

Only use animation where it adds meaning. Approved uses:

```css
/* Scroll reveal — add .reveal to any section, toggle .visible via JS */
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.reveal.visible {
  opacity: 1;
  transform: none;
}

/* Respect reduced motion — always include this */
@media (prefers-reduced-motion: reduce) {
  .reveal { opacity: 1; transform: none; transition: none; }
}
```

Intersection Observer snippet (paste in main.js):
```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.15 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

---

## 7. Image Rules

- All food/gallery images → convert to `.webp` before adding
- Always set explicit width + height on `<img>` to prevent layout shift
- Use `loading="lazy"` on everything below the fold
- Hero image → `loading="eager"` + `fetchpriority="high"`
- Always write descriptive `alt` text: `alt="Paneer tikka served at The Spice Story rooftop, Jodhpur"`

```html
<!-- Hero -->
<img src="hero.webp" alt="Rooftop dining at The Spice Story, Jodhpur" 
     width="1920" height="1080" loading="eager" fetchpriority="high">

<!-- Below fold -->
<img src="dish.webp" alt="Blueberry cheesecake dessert" 
     width="400" height="300" loading="lazy">
```

---

## 8. Accessibility Checklist (per phase)

- [ ] All interactive elements reachable by Tab key
- [ ] Focus ring visible (never `outline: none` without a replacement)
- [ ] Color contrast ≥ 4.5:1 for body text, ≥ 3:1 for large text
- [ ] All images have `alt` text
- [ ] Form inputs have associated `<label>` elements
- [ ] Navigation has `aria-label="Main navigation"`
- [ ] Mobile tap targets ≥ 44×44px

---

## 9. File Structure

```
spice-story/
├── index.html
├── css/
│   ├── reset.css       ← normalize first
│   ├── tokens.css      ← :root variables (from Section 1 above)
│   ├── layout.css      ← grid, section, container
│   ├── components.css  ← card, button, nav, footer
│   └── pages/
│       └── home.css    ← page-specific overrides only
├── js/
│   ├── main.js         ← scroll reveal, nav sticky
│   ├── menu.js         ← tab filter logic
│   └── form.js         ← booking form + validation
├── images/
│   ├── hero/
│   ├── menu/
│   ├── gallery/
│   └── icons/
└── fonts/              ← only if self-hosting
```

---

## 10. Phase-by-Phase Frontend Rules

| Phase | Key rule |
|-------|----------|
| 1 – Hero | Hero image must load in < 2s. Use a compressed WebP, no video autoplay on mobile |
| 2 – About | Keep section padding consistent — use `var(--space-lg)` top/bottom everywhere |
| 3 – Menu | Tab filter must work without page reload. Active tab gets gold underline, not background change |
| 4 – Gallery | Never load all images at once. Paginate or lazy-load in batches of 6 |
| 5 – Reviews | Carousel must not autoplay unless user has not interacted. Pause on hover |
| 6 – Booking | Form must validate client-side before any API call. Show inline errors, not alert() |
| 7 – Polish | Run Lighthouse after every phase. Fix before moving to the next |
