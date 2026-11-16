# talusgis.com

The marketing site for Talus GIS. Plain HTML, one shared stylesheet, no build step, no JavaScript,
no third-party requests. Served by GitHub Pages at the apex `talusgis.com` (the `CNAME` file).

Content © 2026 Talus GIS LLC. The Inter font in `assets/fonts/` is under the SIL Open Font License
(`assets/fonts/OFL.txt`). Nothing in this repository is licensed for reuse.

## Layout

```
index.html              Home — product-first; teaser to Why Talus?
why-talus/              Objection-first: each claim paired with its receipt
how-it-works/           What Talus does, what you need, where it runs; one page per door (databases, …)
how-its-built/          AI provenance: the process and the evidence
editions/               Talus Community vs Talus+, the perpetual-fallback sentence, licensing
compatibility/          ArcGIS Pro, QGIS, QField, GeoLibre, file formats, databases — line by line
faq/                    Mirrors docs/faq.md in the product repository
for/                    Who it's for: index + six pages (park-districts · fire-districts · rural-counties ·
                        conservancies · consultants · outside-the-us), each on the how-it-works three headings
quote/                  What a Talus+ quote request needs to say; a mailto: template
contact/                info@ (sales/general) · support@ · security@
privacy/                One-screen statement (no cookies, no analytics, no third parties)
billing/                Refunds, cancellation, billing questions
404.html                GitHub Pages picks this up automatically
styles.css              The ONE stylesheet. Never add per-page styles.
assets/                 Icon SVGs, favicons, OG image, self-hosted Inter (latin + latin-ext)
CNAME · .nojekyll · robots.txt · sitemap.xml · llms.txt
```

Every page carries the same `<head>`, header/nav, and footer verbatim. That duplication is deliberate:
it keeps an edit a mechanical grep-and-replace across every page. Keep it that way.

## Working rules

- **Plain HTML stays plain.** If something wants a bundler or a generator, that is the trigger to
  reconsider the stack deliberately, not to add a build step quietly.
- **One stylesheet.** Tokens live on `:root` in `styles.css`.
- **No JavaScript** beyond the trivial, and today there is none. The one `<script>` on Home is
  `application/ld+json` structured data — inert data for search engines, not code; keep it that way.
- **Vocabulary:** the editions are *Talus Community* and *Talus+*; air-gapped is a deployment mode of
  either, not an edition. No dollar figure except the published Talus+ price on Editions. The entity is *Talus GIS LLC*. Never a customer,
  municipality, or county named. No screenshots containing real municipal data.
- **No feature grid against ArcGIS.** The positioning is operational simplicity, total cost of
  ownership, and trust, not parity.
- **Every claim is true of the shipped release.** A page is reworded to what is true today rather than
  left promising something that does not exist yet.

## Search engines

What ranks this site is links in and one honest page per question people actually type. On-page, the rules are:

- Every indexable page has a unique `<title>` ending in `— Talus GIS` (the brand as the exact phrase; "Talus" alone is an
  ankle bone and a rock slope), a unique `<meta name="description">` that says the plain thing the page is for, a
  `<link rel="canonical">`, the Open Graph set (`og:type/title/description/url/image/site_name`), and `twitter:card`.
  `privacy/` and `404.html` are `noindex`. Home carries the JSON-LD (`Organization`, `WebSite`, `SoftwareApplication`).
- `sitemap.xml` lists every indexable page; add a line when a page is added. `robots.txt` points at it. `llms.txt` at the
  root summarises the site for AI crawlers; update it when a page is added or renamed.
- No analytics on the page (the privacy statement). The one "did they find us" signal is Google Search Console and Bing
  Webmaster Tools, verified by DNS records, which read nothing from the visitor's browser.

## Local preview

```
python3 -m http.server 8765
```

then open `http://localhost:8765/`. Absolute paths (`/assets/...`) are used throughout, so the
site must be served from its root, not opened as `file://`.
