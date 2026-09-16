<img src="assets/banner.svg" alt="Casey Hsu — full-stack developer, local inference" width="100%">

<p align="center">
  <a href="https://caseyhsu.com">caseyhsu.com</a> ·
  <a href="https://linkedin.com/in/casey-hsu">linkedin</a> ·
  <a href="https://caseyhsu.com/resume.pdf">résumé</a> ·
  <a href="mailto:casey-hsu@outlook.com">email</a>
</p>

```console
$ cat ~/.plan
CMS and e-commerce by day — Shopify, HubSpot, WordPress, Contentful.
Local inference by night — llama.cpp, GGUF quants, and an eval suite
that decides which model gets which job instead of me guessing.
```

I build the client-facing web work and the tooling I use to do it. Right now most of
my spare cycles go into a three-model local stack running on one 10 GB card — not a
fine-tune in sight, just prompts, quants, and measurements.

---

## The lab

Everything below runs on my own workstation. One `llama-server` router, three GGUFs
pulled from HuggingFace, no cloud inference in the loop.

<img src="assets/pipeline.svg" alt="HuggingFace to llama-server router to editors and tools" width="100%">

`./add-model Org/Repo-GGUF` hits the HuggingFace API, lists every GGUF in the repo with
its quant and size, and writes the download plus a builder preset. Model files stage in
`~/models/gguf/`, `make build` generates each model's system prompt and `preset.ini`, and
`make serve` brings up the router with one slot per model and a 10-minute idle sleep that
drops a loaded model from 6226 MiB of VRAM back to 242.

<img src="assets/bench.svg" alt="Generation throughput by model" width="100%">

Those numbers are measured, not vibes — `eval/run-speed.py` on a fixed prompt set, three
models, same sampler. The interesting part isn't generation speed, it's **prompt ingest**:

```
prompt tok/s     lite 2796  ·  gemma 701  ·  qwen 430
```

Agentic tools re-read a ~3k-token system prompt on every single turn, so ingest is what
you actually feel in Cline — which is why the dense 9B that fits entirely in VRAM beats
both MoE models for tool use, despite being the smallest thing in the lineup.

```
gemma   gemma4-26b-a4b-it-qat      32K ctx   21 MoE layers on CPU
qwen    qwen3.6-35b-a3b-mtp        32K ctx   34 MoE layers on CPU, MTP
lite    qwen3.5-9b-mtp Q4_K_M      32K ctx   all GPU — speed anchor + 3rd judge
```

The lineup is three models for a measurement reason, not a speed one: the learn and tutor
suites grade with a leave-one-out judge panel, so two models left exactly one judge per
response and inter-judge disagreement could never be computed. Three means two judges and
a real disagreement number.

> Moved off Ollama to llama.cpp on 2026-09-14. `gemma` and `qwen` are the same weights,
> copied byte for byte out of Ollama's blob store, so their benchmark history carries over.
> `lite` doesn't — Ollama's `qwen3.5:9b` file won't load in llama.cpp, so it was replaced
> with unsloth's MTP build and its scores start fresh.

## Things I'm building

**[Local-LLM](https://github.com/SimBuds/Local-LLM)** — the stack above. Layered Markdown
compiled into system prompts and Modelfiles, per-project overlays at request time, and an
eval suite scoring speed, coding, content, learning, and leak-gated tutoring. No opaque
training runs; every behavior change is version-controlled and reversible.
`llama.cpp` `GGUF` `HuggingFace` `Python` `Make`

**[Jobhunt](https://github.com/SimBuds/Jobhunt)** — local-first job-search CLI. Nine ATS
integrations plus generic RSS over async HTTP with per-source rate limits, durable SQLite
state, and auto-discovery that probes public ATS APIs for new company slugs so curation is
mostly automatic. Fit scoring and document drafting run against the local router with
schema-constrained JSON and deterministic no-fabrication checks. ~700 tests, strict mypy.
I read and submit every application myself.
`Python` `asyncio` `SQLite` `llama-server` `Playwright`

**[SEO-LLM](https://github.com/SimBuds/SEO-LLM)** — no standalone app: Claude Code is the
runtime, the llama.cpp router is the model server, and slash commands sequence ingest →
outline → draft through shell helpers. Lint guards catch banned words, heading hierarchy,
meta length, and JSON-LD before anything ships.
`Claude Code` `llama.cpp` `pandoc` `JSON-LD`

**[Auto-Agent](https://github.com/SimBuds/Auto-Agent)** — FastAPI + Claude API agent.
Postgres for durable memory, Redis for context, a typed capability server bounding what the
agent can actually do. Permission-scoped, recorded, and it survives restarts.
`FastAPI` `Claude API` `Postgres` `Redis` `Docker`

## Things I've shipped

Three-plus years of client work, usually as sole developer and the client's direct point of
contact — scoping through launch and handoff.

**Atelier Dacko** `2023 – now` · WordPress → Shopify migration for a jewelry brand, holding
indexed URLs and organic traffic through full redirect mapping. 16-page storefront on a
customized Dawn theme, plus an LLM content pipeline the editorial team reviews.
→ `−80% drafting time` `+30% organic YoY`

**Neurative AI** `2026` · 8-page HubSpot CMS build from Figma. Reusable editor-configurable
HubL modules so marketing ships without a developer, GitHub Actions CI, clean handoff.
→ `90+ PageSpeed` `−30% load time`

**Geeked Out Goods** `2024` · Python ingest for a 400+ item Shopify catalog — schema-checking
CSV exports before import so malformed feeds never reached the live store.
→ `400+ items` `validated at ingest`

## Stack

```
core      TypeScript · React/Next · Node/Express · Python · PHP/Sass
cms       Shopify (Liquid) · HubSpot (HubL) · WordPress · Contentful · headless
local ai  llama.cpp · GGUF/quants · HuggingFace · MCP · Claude Code · FastAPI
seo       technical SEO · Core Web Vitals · JSON-LD · Search Console · GA4
data      Postgres · MySQL · MongoDB · Redis
devops    Docker · GitHub Actions · Jest · Playwright · AWS · nginx
```

<sub>Contentful Certified Professional · George Brown College, Computer Programming &amp; Analysis (Dean's List) · ten years as a sous chef before all this, which is where the deadline tolerance comes from.</sub>
