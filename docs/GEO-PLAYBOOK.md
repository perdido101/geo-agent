# Practical GEO playbook: MAPROUTE baseline and improvements

MAPROUTE's existing implementation (reported by its owner on October 28, 2026) includes crawler rules, XML sitemap with 39 route pages, SSR pages, maintained llms.txt, Organization/SoftwareApplication/FAQPage JSON-LD, 18 direct-answer FAQ questions, AI-source visit counting and self-reported attribution.

## What the product audits
1. Public HTTPS response and visible HTML returned without JavaScript.
2. Title, meta description, canonical, headings, noindex.
3. JSON-LD presence and parse validity, not schema search-result eligibility.
4. robots.txt rules for OAI-SearchBot, Googlebot, Claude-SearchBot, PerplexityBot.
5. Presence of sitemap.xml and llms.txt (optional convention).
6. Answer-ready FAQ on homepage or /faq.
7. A prioritized, reviewable recommendation queue.

## Next product capabilities to implement
- Parse sitemap entries, audit representative URLs and canonical consistency.
- Compare answers across a fixed prompt set using models with retrieval enabled; store citations, timestamps and locale.
- Prompt clusters for use cases, alternatives, purchase intent, local intent, and competitor comparisons.
- Evidence-backed content audits against competitor pages.
- Search Console / Bing Webmaster / analytics imports, and self-reported attribution.
- Entity consistency, business listings, editorial outreach recommendations.
- CMS diffs with backup/rollback and explicit approvals, scheduled retries and cost limits.
- Transparent uncertainty: mention-rate results are observed samples and are not search rankings.

## Safety and quality
Avoid fake reviews, spam directory submissions, keyword stuffing, misleading JSON-LD, automated Reddit promotion and unverified claims. External visibility improvement requires real earned trust and editorial judgment. Never guarantee AI recommendations.
