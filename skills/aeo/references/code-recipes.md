# AEO code recipes (Next.js App Router shown; principles are generic)

Referenced from SKILL.md's "Code recipes" pointer. These are the fix recipes for
the Findable/Quotable/Understandable/Trustworthy checklist items.

### robots — allow the AI crawlers (the #1 own-goal)

The bots that must be allowed: `GPTBot` (OpenAI), `OAI-SearchBot` (ChatGPT
search), `ChatGPT-User`, `ClaudeBot` / `Claude-Web` (Anthropic), `PerplexityBot`
+ `Perplexity-User`, `Google-Extended` (Gemini/AI Overviews training),
`Applebot-Extended`, `Bytespider`, `CCBot` (Common Crawl, feeds many models).
**Allowing = simply not `Disallow`-ing them.** A blanket `Disallow: /` or a
CMS-default block is what kills AEO. In `app/robots.ts`:

```ts
export default function robots(): MetadataRoute.Robots {
  return {
    rules: [{ userAgent: '*', allow: '/', disallow: ['/api/', '/auth/'] }],
    sitemap: 'https://example.com/sitemap.xml',
    host: 'https://example.com',
  }
}
```

See SKILL.md's Do-Not block: don't gate AI bots by default.

### llms.txt (bonus, but cheap) — a plain-text map for AI

A `/llms.txt` at the root: an H1 with the site name, a blockquote one-liner,
then `##` sections of Markdown links to your key pages with short descriptions.
It's the AI-era `sitemap.xml` in prose. Serve it at the root (a route or a
static file). Keep it current when pages change.

### JSON-LD — the meaning layer

Inject `<script type="application/ld+json">` per page with the right type:

- `Organization` + `WebSite` — once, sitewide (root layout). Name, url, logo, `sameAs` (social profiles), `contactPoint`.
- `Article` / `BlogPosting` — every article. `headline`, `datePublished`, `dateModified`, `author` (a `Person`), `image`, `publisher`.
- `FAQPage` — any page with Q&A sections. Each `Question` + `acceptedAnswer`. This is what surfaces you in "People also ask" and in AI answers directly.
- `Person` — author bios; link from `Article.author`.
- `BreadcrumbList`, `Product`, `Service`, `SoftwareApplication` — where they genuinely fit the page.

See SKILL.md's Do-Not block on schema.

### Canonical + Open Graph — the Next metadata API

```ts
export const metadata: Metadata = {
  title: '…',
  description: '…',                                  // 50–160 chars
  alternates: { canonical: 'https://example.com/page' },
  openGraph: { title, description, url, images: [{ url: '/og.png' }] },
}
```

For localized sites also emit `alternates.languages` (hreflang) so each locale
is its own canonical.

### FAQ-shaping — the highest-leverage content edit

Turn body prose into H2/H3 questions ending in `?`, each answered in one tight,
self-contained paragraph, and mirror them into `FAQPage` schema. This is exactly
what `write-article` already does for meirlabs articles — the answer-engine
structure and the primaryQuestion/answerSummary block. Reuse that pattern.

### Freshness — prove the page is current

Set `dateModified` in the page's JSON-LD **and** `lastmod` in the sitemap, and
bump them on material edits. Stale-looking pages (no date, or >6 months) get
skipped even when the answer is good.

### Measurement — detect AI-referred traffic

In your analytics (PostHog for meirlabs — see `posthog-ops`), segment by
referrer host: `chatgpt.com`, `perplexity.ai`, `gemini.google.com`,
`copilot.microsoft.com`. Track those as a named "AI answer engines" channel and
compare conversion vs. organic. For crawler confirmation, grep server/CDN logs
for the bot user-agents above.
