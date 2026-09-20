<div align="center">

# Mithun Raghu Veluru

Backend engineer, into distributed systems and full stack products.

[Portfolio](https://mithunveluru.is-a.dev) · [GitHub](https://github.com/mithunveluru) · [LinkedIn](https://linkedin.com/in/mithunveluru) · [Email](mailto:mithunveluru7@gmail.com)

</div>

<br>

I like building things that still hold up once real traffic and messy data show up, not just things that work fine with clean seed data. Most of my projects start with one specific problem I want to fix, a slow request path, a store that can double count, a fleet of services that can't agree on state, and then I build the smallest thing that actually closes it.

**Right now:** I'm interning as a Software Engineer at Hanco Automotive in Jeddah, working on a luxury car rental platform end to end. That's the customer site, the booking engine, and the admin tools, built on Next.js, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

More about me and my work is on my site: [mithundev.is-a.dev](https://mithunveluru.is-a.dev/)

---

## Stack

**Languages:** Java, Python, TypeScript, Rust, C++, SQL

**Backend:** Spring Boot, FastAPI, Kafka, Celery, Tauri

**Data:** PostgreSQL, ClickHouse, Redis, Qdrant, SQLite

**Frontend:** Next.js, React, Tailwind CSS

**Infra:** Docker, GitHub Actions, AWS, Vercel, Supabase

**Foundations:** distributed systems, concurrency, system design, data structures and algorithms

---

## Some things I've built

### [Traya](https://github.com/mithunveluru/traya) — observability and incident intelligence
`Java 21` `Kafka` `ClickHouse` `PostgreSQL` `Redis` `OpenTelemetry` `Docker`

Takes in OpenTelemetry signals and turns "checkout latency is high" into a scored, evidence backed root cause guess instead of just another dashboard. Kafka sits in front of ClickHouse as a replayable event backbone, so if something dies mid ingest the consumers just pause and pick back up, and I've got a chaos testing workflow that checks this instead of just claiming it. Under a k6 load test pushing 115K requests in 50 seconds, the gateway shed the 62K over its capacity and processed the remaining 53K with zero failures. Detection runs on ordered rules over robust statistics, no ML in the critical path on purpose.

### [FluxLimit](https://github.com/mithunveluru/fluxlimit) — distributed rate limiting for Java
`Java 21` `Redis` `Spring Boot` `Gradle`

One rate limiting API that works the same whether it's a single JVM or a fleet backed by Redis, published as a real artifact on Maven Central rather than sitting as just another repo. Distributed checks happen as one atomic Lua script timestamped by Redis's own clock, so there's no read modify write race and no manual clock skew handling to worry about. The in-memory store benchmarks at around 4.9M checks per second on a self-cleaning ConcurrentHashMap. It also ships a Spring Boot starter with an `@RateLimit` annotation and an explicit fail open or fail closed policy for when the store goes down.

### [ClearClause](https://github.com/mithunveluru/clearclause) — document risk intelligence
`Python` `FastAPI` `Celery` `Qdrant` `PostgreSQL` `Next.js`

Reads loan, rental, and credit card agreements and traces every risk it flags back to the exact clause behind it. It's deterministic first, a rule engine classifies across 26 document types and drives every finding, and the LLM layer sits strictly downstream so it can't invent a finding on its own. Hybrid retrieval fuses BM25 and vector search with reciprocal rank fusion for the grounded Q&A part. It's backed by 130 backend tests, with ingestion, classification, and retrieval each running as their own separable stage.

### [FlowSight](https://github.com/mithunveluru/flowsight) — behavioral finance platform
`Java 17` `Spring Boot` `PostgreSQL` `Next.js` `React` `Docker` `Tauri`

Turns bank exports and photos of receipts into categorized, forecastable spending, without ever connecting to an actual bank account. Access tokens are short lived (15 minutes) with rotating refresh tokens, and reusing a spent token revokes every live session for that user. Receipt OCR calls a vision LLM for structured extraction with an on device Tesseract fallback, and nothing saves without the user confirming it first. Rate limiting and refresh token state both live in Postgres, so the limits hold across restarts and across instances, not just in memory.

### [Schedora](https://github.com/mithunveluru/schedora) — natural language scheduling
`Next.js` `TypeScript` `Turborepo` `Supabase` `Tauri`

Turns something like "move the standup to after lunch" into a scheduled, conflict checked calendar event. The scheduling engine itself, fuzzy event matching, RFC 5545 recurrence, timezone safe date math, is a standalone package with no database or API dependency, and it's covered by 152 tests across 5 files. It syncs both ways with Google Calendar through push webhooks, and checks for conflicts before writing anything. There's also a Tauri desktop widget alongside the web app.

### [FileLens](https://github.com/mithunveluru/FileLens) — cross platform file manager
`Rust` `Tauri 2` `React` `TypeScript` `SQLite`

A desktop app that shows you what's actually filling up your Downloads folder and lets you clean it up without worrying you'll lose something. Duplicate detection happens in three tiers, size grouping first, then a sampled BLAKE3 fingerprint over three 64KB windows, then a full hash, so most files that aren't actually duplicates never get fully hashed. Hashing runs on a bounded worker pool capped deliberately, since both stages are I/O bound past a certain point. Every destructive action gets previewed and needs explicit confirmation, nothing on disk changes without you saying so.

More projects are up on my [portfolio](https://mithunveluru.is-a.dev/).

---

## Experience

**Software Engineer Intern, Hanco Automotive** — Jeddah, KSA (2026 to present)
Building a luxury car rental platform end to end, customer site, booking engine, and admin tooling, on Next.js, TypeScript, and Supabase.

**Software Engineer Intern, Techvaria** — Bangalore, India (Jun to Jul 2025)

**Certifications:** Oracle Agentic AI Foundations, Oracle AI Database Foundations, OCI AI Foundations, AWS Serverless (Demonstrated)

---

<div align="center">

[Portfolio](https://mithundev.vercel.app) · [GitHub](https://github.com/mithunveluru) · [LinkedIn](https://linkedin.com/in/mithunveluru) · [Email](mailto:mithunveluru7@gmail.com)

</div>
