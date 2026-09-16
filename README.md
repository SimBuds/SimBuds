# Casey Hsu

**Full-stack developer.** CMS, e-commerce, and AI automation tooling.

Toronto, ON · Contentful Certified Professional · open to work.

[caseyhsu.com](https://caseyhsu.com) · [LinkedIn](https://linkedin.com/in/casey-hsu) · [Résumé](https://caseyhsu.com/resume.pdf) · [Email](mailto:casey-hsu@outlook.com)

---

Three-plus years shipping CMS and e-commerce work — usually sole developer and the client's direct point of contact, from scoping through launch and handoff. The other half is applied AI: LLM content pipelines with human review in the loop, and agent tooling on local inference and the Claude API. I run all of it daily, not as demos.

Ten years as a sous chef before this. Calm under deadline comes standard.

## Experience

#### Atelier Dacko — Full-Stack Developer · `2023 – present`

WordPress → Shopify migration with an LLM content pipeline. Migrated site, catalog, redirects, and AWS media while holding indexed URLs and baseline organic traffic; launched a 16-page storefront on a customized Dawn 2.0 theme. Own ongoing content ops and technical SEO. Ring-builder configurator in development.

`−80% drafting time` `+30% organic YoY`

#### Neurative AI — HubSpot CMS Developer · `2026`

8-page HubSpot CMS build from Figma, with reusable editor-configurable HubL modules so marketing ships without a developer. GitHub Actions CI, CRM roles, a month of post-launch QA, clean handoff. Fixed-term, delivered on schedule.

`90+ PageSpeed` `−30% load time`

#### Geeked Out Goods — Shopify Developer · `2024`

Python ingest pipelines for a 400+ item catalog — sanitizing and schema-checking CSV exports before Shopify import, so malformed feeds never reached the live store. Automated inventory updates through the Admin API.

`400+ items` `schema-checked at ingest`

## Projects

#### [Jobhunt](https://github.com/SimBuds/Jobhunt) · `daily use`

Local-first AI job-search CLI. Nine ATS APIs over async HTTP with per-source rate limits, durable SQLite state. Scoring and drafting run on a quantized local model with schema-constrained JSON and deterministic no-fabrication checks. ~700 tests, strict mypy. I submit every application myself.

`Python` `asyncio` `Ollama` `SQLite` `Playwright`

#### [Auto-Agent](https://github.com/SimBuds/Auto-Agent) · `building`

FastAPI + Claude API agent. Postgres for durable memory, Redis for context, a typed capability server bounding what the agent can actually do. Actions are permission-scoped and recorded, never unrestricted. State survives restarts.

`FastAPI` `Claude API` `Postgres` `Redis` `Docker`

#### [Local-LLM](https://github.com/SimBuds/Local-LLM) · `tuning`

Custom Ollama builds compiled from one Markdown tree into generated system prompts and Modelfiles, with per-project overlays injected at request time. An eval suite scores base models on quality, speed, and VRAM. Every behavior change is version-controlled and reversible.

`Qwen3.6` `Gemma4` `Ollama` `Modelfile`

#### [SEO-LLM](https://github.com/SimBuds/SEO-LLM) · `designing`

Content pipeline with lint guards for banned words, heading hierarchy, meta length, and JSON-LD. Search Central RSS triggers rule reviews when a core update lands.

`Claude Code` `Ollama` `Postgres` `JSON-LD`

## Stack

```
core      TypeScript · React/Next · Node/Express · Python · PHP/Sass
cms       Shopify (Liquid) · HubSpot (HubL) · WordPress · Contentful · headless
ai        Ollama · Claude API · MCP · Claude Code · FastAPI
seo       technical SEO · Core Web Vitals · JSON-LD · Search Console · GA4
data      Postgres · MySQL · MongoDB · Redis
devops    Docker · GitHub Actions · Jest · Playwright · AWS · nginx
```

## Education

Contentful Certified Professional — Personalization Skill Badge

George Brown College — Computer Programming & Analysis, Dean's List
