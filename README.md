# Mithun Raghu Veluru

Backend and AI-systems engineer. I build the parts of a product that still have to work after the demo ends.

B.Tech CSE, VIT Vellore '27 · Software Engineer Intern, Hanco Automotive

[Portfolio](https://mithundev.vercel.app) · [Email](mailto:mithunveluru7@gmail.com) · [LinkedIn](https://linkedin.com/in/mithunveluru)

---

## About

I build systems end to end: the pipeline that ingests the data, the API that serves it, and the interface someone actually uses. Four shipped projects span fintech analytics, AI-driven document search, scheduling automation, and a native desktop app. Each one is built the same way — a documented architecture, a containerized dev environment, and a CI pipeline that runs on every push, not a repo that only works on my machine.

I optimize for correctness first, maintainability second, performance third. A slower system I fully understand beats a fast one I have to relearn every time it breaks.

## Engineering Philosophy

- **Architecture before code.** Every project here started as a design decision, not a blank file in an editor.
- **Simple beats clever.** Boring, well-understood patterns have shipped more reliably for me than anything trendy.
- **If it isn't tested, it isn't done.** Schedora ships with 219 passing tests — that's the bar, not the exception.
- **Numbers over adjectives.** Every metric on this page — module counts, thread counts, test counts — is measured, not marketing.
- **Documentation is part of the deliverable**, not something written after the fact for someone else to maintain.

## Currently Exploring

- Consensus and replication in distributed systems
- Observability and incident-response tooling
- Hybrid retrieval and vector search at scale

## What I Build

- **Backend platforms** — APIs and services designed to hold up under real transaction volume, not just a load test.
- **AI-driven systems** — retrieval and RAG pipelines where both accuracy and latency matter.
- **Developer and desktop tooling** — native applications doing CPU-bound work without blocking the UI.
- **Workflow automation** — turning unstructured input into structured, actionable data.

## Tech Stack

**Languages** — Python, Java, TypeScript, C++, Rust, SQL
**Backend** — FastAPI, Spring Boot, Flask, Celery
**Frontend** — React, Next.js, Tauri
**AI / Data** — PyTorch, TensorFlow, scikit-learn, Pandas, Qdrant, RAG pipelines
**Databases** — PostgreSQL, MySQL, MongoDB, Redis, SQLite
**Infrastructure** — Docker, GitHub Actions, AWS, Vercel, Supabase

## Projects

### FlowSight — Behavioral Finance Platform
Java · Spring Boot · PostgreSQL · React · Docker

Automates transaction categorization, spend analysis, and forecasting from raw bank and receipt data.

- **Problem**: Categorizing and reconciling transactions by hand doesn't scale past a handful of accounts, and most tools either lock you into a specific bank integration or hand the work back to you in a spreadsheet.
- **Architecture**: 21 analytics modules sit behind a single API layer. Receipt ingestion runs through OCR as an async job, decoupling upload latency from processing time, with merchant-name normalization applied downstream.
- **Engineering decision**: the ingestion endpoint is rate-limited to protect the OCR pipeline from bursty uploads without dropping requests.
- [Repository](https://github.com/mithunveluru/flowsight)

<!-- docs/images/flowsight-architecture.png -->

### ClearClause — AI Document Intelligence
Python · FastAPI · Celery · Qdrant · PostgreSQL · Next.js

RAG-powered analysis for legal documents, built around hybrid retrieval rather than pure vector search.

- **Problem**: Pure semantic search misses exact-match clauses (dates, defined terms, section references) that legal review depends on; pure keyword search misses paraphrased intent.
- **Architecture**: hybrid vector + keyword search across 26 document types, with async ingestion, retrieval, and entity extraction running as separate pipeline stages so a slow extraction job doesn't block search availability.
- **Engineering decision**: entity extraction runs on isolated Celery workers, so retrieval latency doesn't inherit extraction latency.
- [Repository](https://github.com/mithunveluru/clearclause)

<!-- docs/images/clearclause-architecture.png -->

### Schedora — AI Scheduling Platform
Next.js 14 · Supabase · Google Calendar API · Turborepo

Converts natural language into conflict-free calendar events, with multi-tenant isolation built in from the schema up.

- **Problem**: Most scheduling tools assume a single tenant or bolt multi-tenancy on after the fact, which tends to surface later as data leaking across accounts.
- **Architecture**: OAuth 2.0 authentication, 11 row-level-security policies enforcing tenant isolation at the database layer, and 20 REST API routes covering the scheduling surface.
- **Testing**: 219 passing tests.
- [Live demo](https://schedora-web.vercel.app)

<!-- docs/images/schedora-architecture.png -->

### FileLens — Cross-Platform File Manager
Rust · Tauri 2 · React 19 · TypeScript · SQLite

Native desktop app for large-scale duplicate-file cleanup.

- **Problem**: Hashing and comparing large file sets on a single thread is slow enough to make a cleanup tool unusable on the datasets people actually need to clean.
- **Architecture**: a concurrent duplicate-detection engine using BLAKE3 hashing across an 8-thread worker pool, native IPC between the Rust backend and React frontend, and local persistence via SQLite.
- **Engineering decision**: BLAKE3 over SHA-256, for the throughput difference at the hash volumes this tool processes.
- [Repository](https://github.com/mithunveluru/FileLens)

<!-- docs/images/filelens-architecture.png -->

More detail on each project at [mithundev.vercel.app](https://mithundev.vercel.app).

## Engineering Quality

Every repository above ships with:

- A documented architecture, including the reasoning behind key design decisions
- A Docker-based local development environment
- CI running on every push
- Project-level READMEs that explain scope and tradeoffs, not just setup steps

Where a project's scope calls for it, this extends further — Schedora, for example, carries a full test suite covering its API surface.

## Experience

**Software Engineer Intern — Hanco Automotive** (Jeddah, KSA) · May 2026 – Present
Building a luxury car-rental platform end to end — customer-facing site, booking engine, and admin tooling — on Next.js 14, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

**Software Engineer Intern — Techvaria** (Bangalore, IN) · Jun 2025 – Jul 2025

## Certifications

- Oracle Agentic AI Foundations
- OCI AI Foundations
- Oracle AI Database Foundations
- AWS Serverless (Demonstrated)

---

[Portfolio](https://mithundev.vercel.app) · [Email](mailto:mithunveluru7@gmail.com) · [LinkedIn](https://linkedin.com/in/mithunveluru)
