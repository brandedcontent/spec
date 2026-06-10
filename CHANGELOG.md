# Changelog

All notable changes to the Agentic Branded Content spec are recorded here.
The spec follows a simple `MAJOR.MINOR` version: `MINOR` for additive or
clarifying changes, `MAJOR` once the `abc.txt` format and fragment contract
are frozen.

## 0.1 — 2026-06-10

First public draft of Agentic Branded Content (ABC).

- `abc.txt` declaration format (provider lines, `DIRECT`/`RESELLER`, optional directives).
- Brand **card** delivery: `<article role="complementary" class="abc-card">`, ~2 KB, under
  1 000 tokens. The deliverable is the **card**; "fragment" refers only to the provider's
  **fragment endpoint** (the channel the edge calls).
- Fragment endpoint behavior contract (`200` card / `204` no-fill, cacheable by URL;
  `format=both` returns a JSON envelope `{ card, html }`). Classification is done at the
  publisher's edge, which calls the endpoint for AI-agent traffic only — so the response
  carries no `Vary: User-Agent`.
- Card JSON schema and a vendor-verified known-agents list (HTTP User-Agent markers, not
  robots.txt control tokens), with agent-verification guidance (reverse-DNS, published IP
  ranges, CDN verified-bot signals) as the site's responsibility.
- Reference adapters: ESI (Varnish/Fastly/Akamai), Cloudflare Worker, Lambda@Edge, browser JS.
