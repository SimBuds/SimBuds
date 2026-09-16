<h1 align="center">Casey Hsu</h1>

<p align="center">
  <b>Full-Stack Developer</b> · CMS, E-Commerce &amp; AI Automation Tooling<br>
  <sub>Toronto, ON (ET) · Contentful Certified Professional</sub>
</p>

<p align="center">
  <a href="https://caseyhsu.com"><img src="https://img.shields.io/badge/caseyhsu.com-111111?style=flat-square&logo=astro&logoColor=white" alt="Website"></a>
  <a href="https://linkedin.com/in/casey-hsu"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="mailto:casey-hsu@outlook.com"><img src="https://img.shields.io/badge/Email-333333?style=flat-square&logo=maildotru&logoColor=white" alt="Email"></a>
  <a href="https://caseyhsu.com/resume.pdf"><img src="https://img.shields.io/badge/Résumé-PDF-B04A2F?style=flat-square" alt="Resume"></a>
</p>

---

```console
$ whoami
casey — full-stack dev, 3+ yrs independent client delivery
$ cat ~/.focus
CMS & e-commerce builds (Shopify · HubSpot · WordPress · Contentful)
applied AI (LLM content pipelines · local inference · agent tooling)
$ status
open to full-stack / CMS / e-commerce / applied-AI roles — GTA or remote in Canada
```

Most of my client work is **CMS and e-commerce**: custom themes, platform migrations,
editor-friendly modules, technical SEO, QA, launch, and clean handoff — usually as sole
developer and the client's direct point of contact.

The other half is **applied AI**: LLM content pipelines that keep human review in the loop,
and agentic tooling on local inference (Ollama) and the Claude API. I run all of it in my own
workflow every day, not as a demo.

Before this I spent ten years as a **sous chef** and team lead running kitchens of 5–20 —
hiring, training, scheduling, food-cost budgeting — carried through my diploma and first dev
contracts. Calm under deadline comes standard.

---

### 01 · Now

| Project | What it is | Stack |
| --- | --- | --- |
| **[Jobhunt](https://github.com/SimBuds/Jobhunt)** <br> `daily use` | Local-first AI job-search CLI. Nine public ATS APIs (Greenhouse, Lever, Ashby, Workday, SmartRecruiters, Workable, Recruitee, Adzuna, Job Bank Canada) run concurrently over async HTTP with per-source rate limits against durable SQLite. Fit scoring and doc drafting run on a quantized local model with schema-constrained JSON and deterministic no-fabrication checks against a verified profile. ~700 tests, Ruff, strict mypy. I review and submit every application myself. | `Python` `asyncio` `Ollama` `SQLite` `Playwright` `mypy` |
| **[Auto-Agent](https://github.com/SimBuds/Auto-Agent)** <br> `building` | FastAPI + Claude API agent. Postgres holds durable memory, Redis caches context, and a typed capability server bounds what the agent can actually do — actions are permission-scoped and recorded for review, never run unrestricted. State survives restarts. Runs continuously on Docker Compose on my own Arch box. | `FastAPI` `Claude API` `Postgres` `Redis` `Docker` |
| **[Local-LLM](https://github.com/SimBuds/Local-LLM)** <br> `tuning` | AI context stack: custom Ollama builds compiled from one shared Markdown tree into generated system prompts and Modelfiles, with per-project overlays injected at request time. An eval suite scores base models on output quality, speed, and VRAM. Tuned around q5_0 KV cache, flash attention, 16k context. Every behavior change is version-controlled and reversible. | `Qwen3.6` `Gemma4` `Ollama` `Modelfile` |
| **[SEO-LLM](https://github.com/SimBuds/SEO-LLM)** <br> `designing` | Hybrid Claude Code + local-model SEO stack. Claude Code plans; lint guards catch banned words, heading hierarchy, meta length, and JSON-LD schema; Google Search Central RSS triggers rule reviews when a core update lands. | `Claude Code` `Ollama` `Postgres` `JSON-LD` |

---

### 02 · Client Work

**Atelier Dacko** — *Full-Stack Developer · Apr 2023 – Present*
WordPress → Shopify migration with an LLM content pipeline. Sole developer and client contact:
migrated site, catalog, URL redirects, and AWS-hosted media while preserving indexed URLs and
baseline organic traffic through full redirect mapping and post-launch Search Console monitoring,
then launched a 16-page storefront on a customized Dawn 2.0 theme. Built an LLM pipeline that
drafts product copy and content briefs for the client's editorial team, then audits published
output against target keywords. I own ongoing content ops and on-page technical SEO. A
ring-builder configurator is in active development.
`16 pages` · `−80% drafting time` · `+30% organic YoY`

**Neurative AI** — *HubSpot CMS Developer · Jan – Apr 2026*
Custom 8-page HubSpot CMS site from Figma designs, with reusable editor-configurable HubL modules
and templates so marketing could ship content without developer involvement. Image optimization,
lazy loading, and caching cut load time 30% and kept PageSpeed above 90. GitHub Actions CI with
automated linting, CRM roles and permissions, and a month of post-launch QA through to clean
handoff. Fixed-term contract, completed on schedule.
`8 pages` · `90+ PageSpeed` · `−30% load time`

**Geeked Out Goods** — *Shopify Developer · Jan – May 2024*
Python pipelines for bulk product uploads across a 400+ item vintage gaming catalog — sanitizing
and schema-checking CSV inventory exports before Shopify import, so malformed feeds never reached
the live store. Integrated third-party apps and the Shopify Admin API to automate inventory and
product updates previously handled by hand.
`400+ items` · `Python ingest` · `schema checks`

---

### 03 · Stack

**Core** &nbsp;`JavaScript / TypeScript` `React · Next.js` `Node.js · Express` `Python` `PHP · Sass`

**CMS & E-commerce** &nbsp;`Shopify (Liquid)` `HubSpot (HubL)` `WordPress` `Contentful` `Headless`

**AI & Tooling** &nbsp;`Ollama` `Claude API` `Model Context Protocol` `Claude Code CLI` `FastAPI` `Codex`

**SEO & Analytics** &nbsp;`Technical SEO` `Core Web Vitals` `JSON-LD` `Search Console` `GA4 · Google Ads`

**Data & DevOps** &nbsp;`PostgreSQL · MySQL` `MongoDB · Redis` `Docker` `GitHub Actions` `Jest · Playwright` `AWS · Azure` `nginx · Lightsail`

---

### 04 · By the numbers

| | |
| --- | --- |
| **3+ yrs** | Independent client delivery |
| **−80%** | Content drafting time via LLM pipeline |
| **+30%** | Organic blog traffic YoY on Shopify |
| **90+** | PageSpeed after HubSpot launch |

---

### 05 · Credentials

- **Contentful Certified Professional** — with Personalization Skill Badge
- **George Brown College** — Computer Programming & Analysis, Dean's List (all terms)

---

<p align="center">
  <sub>
    <a href="https://caseyhsu.com">caseyhsu.com</a> · built with Astro, served by nginx on AWS Lightsail<br>
    Open to contract, hybrid, or on-site — GTA or remote within Canada.
  </sub>
</p>
