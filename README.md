<div align="center">

# Mithun Raghu Veluru

**Software Engineer · Backend & Distributed Systems · Full-Stack**

![Role](https://img.shields.io/badge/Software%20Engineer%20Intern-161b22?style=flat-square)
![Education](https://img.shields.io/badge/VIT%20Vellore%20%C2%B7%20%2727-161b22?style=flat-square)

[![Portfolio](https://img.shields.io/badge/Portfolio-161b22?style=flat-square&logo=vercel&logoColor=white)](https://mithundev.vercel.app)
[![Email](https://img.shields.io/badge/Email-161b22?style=flat-square&logo=gmail&logoColor=white)](mailto:mithunveluru7@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-161b22?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/mithunveluru)
[![GitHub](https://img.shields.io/badge/GitHub-161b22?style=flat-square&logo=github&logoColor=white)](https://github.com/mithunveluru)

</div>

<br>

Backend systems, developer tooling, and full-stack products — the kind that still have to behave once real traffic and messy data show up, not just the seed data. Most of what's below is me picking one failure mode (a slow request path, a store that can double-count, a fleet that can't agree on state) and building the smallest thing that actually closes it.

<div align="center">

| | |
|---|---|
| **Currently** | Booking engine & admin tooling for a luxury car-rental platform — Hanco Automotive, Jeddah |
| **Digging into** | Distributed systems, hybrid retrieval, observability |

</div>

---

## Stack

**Languages**
![Java](https://img.shields.io/badge/Java-161b22?style=flat-square&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-161b22?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-161b22?style=flat-square&logo=typescript&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-161b22?style=flat-square&logo=rust&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-161b22?style=flat-square&logo=cplusplus&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-161b22?style=flat-square)

**Backend & systems**
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-161b22?style=flat-square&logo=spring&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-161b22?style=flat-square&logo=fastapi&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-161b22?style=flat-square&logo=apachekafka&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-161b22?style=flat-square&logo=celery&logoColor=white)
![Tauri](https://img.shields.io/badge/Tauri-161b22?style=flat-square&logo=tauri&logoColor=white)

**Data**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-161b22?style=flat-square&logo=postgresql&logoColor=white)
![ClickHouse](https://img.shields.io/badge/ClickHouse-161b22?style=flat-square&logo=clickhouse&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-161b22?style=flat-square&logo=redis&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-161b22?style=flat-square)
![SQLite](https://img.shields.io/badge/SQLite-161b22?style=flat-square&logo=sqlite&logoColor=white)

**Frontend**
![Next.js](https://img.shields.io/badge/Next.js-161b22?style=flat-square&logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-161b22?style=flat-square&logo=react&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-161b22?style=flat-square&logo=tailwindcss&logoColor=white)

**Infra**
![Docker](https://img.shields.io/badge/Docker-161b22?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-161b22?style=flat-square&logo=githubactions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-161b22?style=flat-square&logo=amazonaws&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-161b22?style=flat-square&logo=vercel&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-161b22?style=flat-square&logo=supabase&logoColor=white)

**Foundations**
`Distributed Systems` `Concurrency` `System Design (HLD/LLD)` `Data Structures & Algorithms`

---

## Selected work

### Traya — observability & incident intelligence
[![CI](https://github.com/mithunveluru/traya/actions/workflows/ci.yml/badge.svg)](https://github.com/mithunveluru/traya/actions/workflows/ci.yml)
[![Integration](https://github.com/mithunveluru/traya/actions/workflows/integration.yml/badge.svg)](https://github.com/mithunveluru/traya/actions/workflows/integration.yml)

Ingests OpenTelemetry signals and turns *"checkout latency is high"* into a scored, evidence-backed root-cause hypothesis instead of a wall of dashboards.

`Java 21` `Kafka` `ClickHouse` `PostgreSQL` `Redis` `OpenTelemetry` `Docker`

- Kafka sits in front of ClickHouse as a replayable event backbone — an outage mid-ingest just pauses consumers, verified by a dedicated chaos-testing workflow rather than a claim.
- A k6 load test pushed 115K requests in 50s past the gateway's limit: it shed 62K over capacity and processed the remaining 53K at a 0% failure rate.
- Detection runs on ordered rules over robust statistics (median/MAD baselines) — deliberately no ML in the critical path.

[View repository ↗](https://github.com/mithunveluru/traya)

### FluxLimit — distributed rate limiting for Java
[![Build](https://github.com/mithunveluru/fluxlimit/actions/workflows/build.yml/badge.svg)](https://github.com/mithunveluru/fluxlimit/actions/workflows/build.yml)
[![Maven Central](https://img.shields.io/maven-central/v/io.github.mithunveluru/fluxlimit-core?color=161b22&label=Maven%20Central)](https://central.sonatype.com/artifact/io.github.mithunveluru/fluxlimit-core)

One rate-limiting API from a single JVM to a Redis-backed fleet — published as a real Maven Central artifact, not just a repo.

`Java 21` `Redis` `Spring Boot` `Gradle`

- Distributed checks run as one atomic Lua script timestamped by Redis's own clock — no read-modify-write race, no manual clock-skew handling.
- In-memory store benchmarks at roughly 4.9M checks/sec on a self-cleaning `ConcurrentHashMap`.
- Ships a Spring Boot starter (`@RateLimit`, SpEL keys) with an explicit, flagged fail-open/fail-closed policy for when the store is down.

[View repository ↗](https://github.com/mithunveluru/fluxlimit)

### ClearClause — document risk intelligence
[![CI](https://github.com/mithunveluru/clearclause/actions/workflows/ci.yml/badge.svg)](https://github.com/mithunveluru/clearclause/actions/workflows/ci.yml)

Reads loan, rental, and credit-card agreements and traces every flagged risk back to the exact clause that produced it.

`Python` `FastAPI` `Celery` `Qdrant` `PostgreSQL` `Next.js`

- Deterministic-first: a rule engine classifies across 26 document types and drives every finding; the LLM layer sits strictly downstream and can't introduce a finding on its own.
- Hybrid retrieval fuses BM25 and vector search with Reciprocal Rank Fusion for the grounded Q&A layer.
- 130 backend tests; ingestion, classification, and retrieval each run as separable pipeline stages.

[View repository ↗](https://github.com/mithunveluru/clearclause)

### FlowSight — behavioral finance platform
[![CI](https://github.com/mithunveluru/flowsight/actions/workflows/ci.yml/badge.svg)](https://github.com/mithunveluru/flowsight/actions/workflows/ci.yml)

Turns bank exports and receipt photos into categorized, forecastable spend — without ever connecting to a bank account.

`Java 17` `Spring Boot` `PostgreSQL` `Next.js` `React` `Docker` `Tauri`

- Short-lived (15 min) access tokens with rotating refresh tokens; reusing a spent token revokes every live session for that user.
- Receipt OCR calls a vision LLM for structured extraction, with an in-image Tesseract fallback and a review-first workflow — nothing saves without confirmation.
- Rate limiting and refresh-token state both live in Postgres, so limits hold across restarts and instances, not just in memory.

[View repository ↗](https://github.com/mithunveluru/flowsight)

### Schedora — natural-language scheduling
[![CI](https://github.com/mithunveluru/schedora/actions/workflows/ci.yml/badge.svg)](https://github.com/mithunveluru/schedora/actions/workflows/ci.yml)

Turns *"move the standup to after lunch"* into a scheduled, conflict-checked calendar event.

`Next.js` `TypeScript` `Turborepo` `Supabase` `Tauri`

- The scheduling engine (fuzzy event matching, RFC 5545 recurrence, timezone-safe date math) is a standalone package with no DB or API dependency — 152 tests across 5 files, fully isolated.
- Bidirectional Google Calendar sync via push webhooks, with conflicts checked before anything is written.
- Ships a Tauri desktop widget alongside the Next.js web app.

[View repository ↗](https://github.com/mithunveluru/schedora)

### FileLens — cross-platform file manager
[![CI](https://github.com/mithunveluru/FileLens/actions/workflows/ci.yml/badge.svg)](https://github.com/mithunveluru/FileLens/actions/workflows/ci.yml)

A desktop app that explains what's actually filling your Downloads folder and lets you clean it up safely.

`Rust` `Tauri 2` `React` `TypeScript` `SQLite`

- Three-tier duplicate detection — size grouping, then a sampled BLAKE3 fingerprint over three 64KB windows, then a full hash — so most non-duplicates never get fully hashed.
- Hashing runs on a bounded worker pool (`min(available_parallelism(), 8)`), capped deliberately since both stages are I/O-bound past a point.
- Every destructive action is previewed and requires explicit confirmation; nothing on disk changes silently.

[View repository ↗](https://github.com/mithunveluru/FileLens)

More at [mithundev.vercel.app](https://mithundev.vercel.app).

---

## Activity

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/mithunveluru/mithunveluru/output/github-snake-dark.svg" />
  <img alt="GitHub contribution snake" src="https://raw.githubusercontent.com/mithunveluru/mithunveluru/output/github-snake.svg" width="100%" />
</picture>

![GitHub followers](https://img.shields.io/github/followers/mithunveluru?style=flat-square&label=Followers&color=161b22)

## Experience

**2026 → present** — Software Engineer Intern, **Hanco Automotive**, Jeddah, KSA
Building a luxury car-rental platform end to end — customer site, booking engine, admin tooling — on Next.js, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

**2025 (Jun–Jul)** — Software Engineer Intern, **Techvaria**, Bangalore, India

**Certifications:** `Oracle Agentic AI Foundations` · `Oracle AI Database Foundations` · `OCI AI Foundations` · `AWS Serverless (Demonstrated)`

---

<div align="center">

[![Portfolio](https://img.shields.io/badge/Portfolio-161b22?style=flat-square&logo=vercel&logoColor=white)](https://mithundev.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-161b22?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/mithunveluru)
[![Email](https://img.shields.io/badge/Email-161b22?style=flat-square&logo=gmail&logoColor=white)](mailto:mithunveluru7@gmail.com)

</div>
