# SEO SKILL — The Spice Story Website
> Keep this file in your project root. Run through it once per phase before deploying.

---

## 1. Meta Tags (paste in every HTML `<head>`)

```html
<!-- Primary Meta -->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Spice Story | Best Vegetarian Restaurant & Rooftop Fine Dine in Jodhpur</title>
<meta name="description" content="Experience authentic vegetarian fine dining at The Spice Story, Jodhpur's top-rated rooftop restaurant. 4.7★ on Google. Book your table today. ₹400–600/person.">
<meta name="keywords" content="vegetarian restaurant Jodhpur, rooftop restaurant Jodhpur, fine dining Jodhpur, best veg restaurant Jodhpur, The Spice Story">
<link rel="canonical" href="https://www.thespicestory.com/">

<!-- Open Graph (WhatsApp, Facebook preview) -->
<meta property="og:type" content="restaurant">
<meta property="og:title" content="The Spice Story | Rooftop Fine Dine Jodhpur">
<meta property="og:description" content="4.7★ rated vegetarian fine dining on a rooftop in the heart of Jodhpur. Book a table today.">
<meta property="og:image" content="https://www.thespicestory.com/images/og-cover.webp">
<meta property="og:url" content="https://www.thespicestory.com/">
<meta property="og:locale" content="en_IN">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="The Spice Story | Rooftop Fine Dine Jodhpur">
<meta name="twitter:description" content="Best vegetarian fine dining in Jodhpur. 4.7★ · ₹400–600 · Rooftop.">
<meta name="twitter:image" content="https://www.thespicestory.com/images/og-cover.webp">

<!-- Geo tags (local SEO) -->
<meta name="geo.region" content="IN-RJ">
<meta name="geo.placename" content="Jodhpur">
<meta name="geo.position" content="26.279327;73.037535">
<meta name="ICBM" content="26.279327, 73.037535">
```

---

## 2. Schema.org JSON-LD (paste before `</body>`)

This is the single most important SEO task for a local restaurant. Google uses this to show your rating, price range, hours, and address directly in search results.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "The Spice Story",
  "alternateName": "द स्पाइस स्टोरी",
  "description": "Best vegetarian family restaurant with fine dine and rooftop in Jodhpur, Rajasthan.",
  "url": "https://www.thespicestory.com",
  "telephone": "+919001890329",
  "priceRange": "₹₹",
  "servesCuisine": ["Indian", "Vegetarian", "Continental"],
  "menu": "https://www.thespicestory.com/menu",
  "hasMap": "https://maps.google.com/?cid=YOUR_GOOGLE_CID",
  "image": [
    "https://www.thespicestory.com/images/gallery/rooftop.webp",
    "https://www.thespicestory.com/images/gallery/interior.webp"
  ],
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "3rd Floor, Plot No. 3, East Patel Nagar, Circuit House Road",
    "addressLocality": "Ratanada, Jodhpur",
    "addressRegion": "Rajasthan",
    "postalCode": "342011",
    "addressCountry": "IN"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 26.279327,
    "longitude": 73.037535
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "reviewCount": "3308",
    "bestRating": "5"
  },
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"],
      "opens": "11:00",
      "closes": "23:30"
    }
  ],
  "amenityFeature": [
    { "@type": "LocationFeatureSpecification", "name": "Rooftop Seating", "value": true },
    { "@type": "LocationFeatureSpecification", "name": "Fine Dining", "value": true },
    { "@type": "LocationFeatureSpecification", "name": "Dine-in", "value": true },
    { "@type": "LocationFeatureSpecification", "name": "No Contact Delivery", "value": true }
  ]
}
</script>
```

---

## 3. Heading Hierarchy (follow this exactly)

One `<h1>` per page only. Never skip levels.

```
<h1>  The Spice Story — one per page, in the hero
<h2>  Section titles: "Our Story", "Our Menu", "Gallery", "Reserve a Table"
<h3>  Sub-sections: dish category names, individual review headings
<h4>  Card titles: individual dish names, experience names
```

Bad:  `<h1>` → `<h3>` (skipped h2)
Good: `<h1>` → `<h2>` → `<h3>` → `<h4>`

---

## 4. URL Structure

```
/                    ← homepage (all sections)
/menu                ← full menu page (for PDF or separate page)
/gallery             ← gallery page (if separated)
/reserve             ← reservation page (if separated)
/contact             ← contact + map
```

Rules:
- Lowercase only, hyphens not underscores
- No `/page1`, `/index2.html` type names
- Add `<link rel="canonical">` on every page

---

## 5. Image SEO

Every image needs:
```html
<!-- Format: [dish/location] at [restaurant name], [city] -->
<img 
  src="paneer-tikka.webp"
  alt="Paneer tikka starter at The Spice Story restaurant, Jodhpur"
  width="600" 
  height="400"
  loading="lazy"
>
```

File naming rules:
- `paneer-tikka.webp` ✅
- `IMG_20240312.jpg` ❌
- `dish1.png` ❌

---

## 6. Page Speed Checklist (run before every deploy)

- [ ] All images converted to `.webp`
- [ ] Images have explicit `width` and `height` (prevents CLS)
- [ ] Hero image uses `loading="eager" fetchpriority="high"`
- [ ] CSS minified (use VSCode extension or `cleancss`)
- [ ] JS deferred: `<script src="main.js" defer></script>`
- [ ] Google Fonts loaded with `display=swap`
- [ ] No render-blocking resources in `<head>` except critical CSS
- [ ] Gzip/Brotli enabled on Vercel/Netlify (automatic)

Target scores on Lighthouse:
| Metric | Target |
|--------|--------|
| Performance | ≥ 90 |
| Accessibility | ≥ 95 |
| Best Practices | ≥ 95 |
| SEO | 100 |

---

## 7. Local SEO Checklist (do once, not per page)

- [ ] Google Business Profile claimed and verified
- [ ] NAP consistent everywhere (Name, Address, Phone) — same format on website, Google, Zomato, Swiggy
- [ ] Add website URL to Google Business Profile
- [ ] Upload 10+ photos to Google Business Profile
- [ ] Enable Google Reserve (already active per listing)
- [ ] Submit sitemap to Google Search Console
- [ ] Add business to: Justdial, Sulekha, IndiaMart

---

## 8. sitemap.xml (create at project root)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.thespicestory.com/</loc>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://www.thespicestory.com/menu</loc>
    <changefreq>monthly</changefreq>
    <priority>0.9</priority>
  </url>
  <url>
    <loc>https://www.thespicestory.com/gallery</loc>
    <changefreq>monthly</changefreq>
    <priority>0.7</priority>
  </url>
  <url>
    <loc>https://www.thespicestory.com/reserve</loc>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

---

## 9. robots.txt (create at project root)

```
User-agent: *
Allow: /
Sitemap: https://www.thespicestory.com/sitemap.xml
```

---

## 10. SEO Per Phase — What to Check

| Phase | SEO task |
|-------|----------|
| 1 – Hero | `<h1>` set, meta title/desc written, canonical added |
| 2 – About | Alt text on all About section images |
| 3 – Menu | Each dish name in `<h4>`, price visible as text (not image) |
| 4 – Gallery | All gallery images named correctly, alt tags written |
| 5 – Reviews | Review schema added if embedding Google reviews |
| 6 – Booking | Form has proper `<label>` for every field |
| 7 – Polish | sitemap.xml live, submitted to Search Console, Lighthouse SEO = 100 |
