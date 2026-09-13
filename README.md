<div align="center">

# Mithun Raghu Veluru

![Role](https://img.shields.io/badge/Software%20Engineer%20Intern-161b22?style=flat-square)
![Education](https://img.shields.io/badge/VIT%20Vellore%202027-161b22?style=flat-square)

[![Portfolio](https://img.shields.io/badge/Portfolio-161b22?style=flat-square&logo=vercel&logoColor=white)](https://mithundev.vercel.app)
[![Email](https://img.shields.io/badge/Email-161b22?style=flat-square&logo=gmail&logoColor=white)](mailto:mithunveluru7@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-161b22?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/mithunveluru)
[![GitHub](https://img.shields.io/badge/GitHub-161b22?style=flat-square&logo=github&logoColor=white)](https://github.com/mithunveluru)

</div>

<br>

I'm a CS student at VIT Vellore (class of 2027), currently interning at Hanco Automotive in Jeddah, where I'm building the booking engine and admin tooling behind a luxury car-rental platform. Most of my other projects live in the same general area — backend systems, data pipelines, and the unglamorous plumbing that keeps an app working once real users and real data show up.

I like picking a problem, figuring out where it actually breaks, and building the smallest thing that fixes that specific part well. A lot of what's below came out of that: decoupling a slow job from the request path, isolating a flaky worker so it can't take the rest of the system down with it, that kind of thing.

---

## At a glance

| | |
|---|---|
| **Building** | Booking engine and admin tooling for a car-rental platform, at Hanco Automotive |
| **Shipped** | FlowSight · ClearClause · Schedora · FileLens |
| **Reading up on** | Distributed systems, hybrid retrieval, observability |

## Projects

### FlowSight — behavioral finance platform
`Java · Spring Boot · PostgreSQL · React · Docker`

Started this because categorizing bank and receipt data by hand stops being feasible once you're past a handful of accounts, and most tools that promise to automate it either lock you into their own bank integrations or just hand the mess back to you as a spreadsheet.

FlowSight ingests raw transaction and receipt data and turns it into categorized, forecastable spend across 21 analytics modules. The one design choice I'd point to: receipt OCR runs as an async job rather than inline with the upload, so uploading a receipt doesn't mean waiting on a pipeline that might be slow. The ingestion endpoint is also rate-limited, so a burst of uploads can't take the OCR workers down with it.

[View repository ↗](https://github.com/mithunveluru/flowsight)

### ClearClause — AI document intelligence
`Python · FastAPI · Celery · Qdrant · PostgreSQL · Next.js`

Semantic search is good at finding documents that mean the same thing, and bad at finding the exact clause, date, or defined term you're actually looking for. Keyword search has the opposite problem. ClearClause runs both — hybrid vector-and-keyword retrieval over legal documents, covering 26 document types.

Ingestion, retrieval, and entity extraction each run as their own pipeline stage, with entity extraction on isolated Celery workers, so a slow extraction job never becomes the reason search feels slow. Getting retrieval quality and retrieval latency to fail independently of each other turned out to matter as much as the retrieval algorithm itself.

[View repository ↗](https://github.com/mithunveluru/clearclause)

### Schedora — AI scheduling platform
`Next.js 14 · Supabase · Google Calendar API · Turborepo`

A lot of scheduling tools are built single-tenant first and get multi-tenancy added later, which is usually how you end up with one account's data leaking into another's. Schedora turns natural-language requests into conflict-free calendar events, and enforces tenant isolation with 11 row-level-security policies at the database layer — not the application layer — across 20 API routes.

It also ships with 219 passing tests. Not because the project needed that many, but because a scheduling tool that's occasionally wrong about a meeting time is worse than one that just does less.

[View live demo ↗](https://schedora-web.vercel.app)

### FileLens — cross-platform file manager
`Rust · Tauri 2 · React 19 · TypeScript · SQLite`

Hashing and comparing a large set of files on a single thread is slow enough that a duplicate-cleanup tool becomes a tool you stop bothering to open. FileLens is a native desktop app — Rust backend, React frontend over Tauri — with a concurrent detection engine that spreads BLAKE3 hashing across an 8-thread worker pool. Native IPC between Rust and the UI keeps the interface responsive mid-hash. I went with BLAKE3 over SHA-256 deliberately, for the throughput difference at the volumes this actually runs at.

[View repository ↗](https://github.com/mithunveluru/FileLens)

More detail on each at [mithundev.vercel.app](https://mithundev.vercel.app).

## Stack

**Languages**
![Python](https://img.shields.io/badge/Python-161b22?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-161b22?style=flat-square&logo=openjdk&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-161b22?style=flat-square&logo=typescript&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-161b22?style=flat-square&logo=cplusplus&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-161b22?style=flat-square&logo=rust&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-161b22?style=flat-square)

**Backend**
![FastAPI](https://img.shields.io/badge/FastAPI-161b22?style=flat-square&logo=fastapi&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-161b22?style=flat-square&logo=spring&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-161b22?style=flat-square&logo=flask&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-161b22?style=flat-square&logo=celery&logoColor=white)

**Frontend**
![React](https://img.shields.io/badge/React-161b22?style=flat-square&logo=react&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-161b22?style=flat-square&logo=nextdotjs&logoColor=white)
![Tauri](https://img.shields.io/badge/Tauri-161b22?style=flat-square&logo=tauri&logoColor=white)

**AI / Data**
![PyTorch](https://img.shields.io/badge/PyTorch-161b22?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-161b22?style=flat-square&logo=tensorflow&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-161b22?style=flat-square&logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-161b22?style=flat-square&logo=pandas&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-161b22?style=flat-square)

**Databases**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-161b22?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-161b22?style=flat-square&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-161b22?style=flat-square&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-161b22?style=flat-square&logo=redis&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-161b22?style=flat-square&logo=sqlite&logoColor=white)

**Infrastructure**
![Docker](https://img.shields.io/badge/Docker-161b22?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-161b22?style=flat-square&logo=githubactions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-161b22?style=flat-square&logo=amazonaws&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-161b22?style=flat-square&logo=vercel&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-161b22?style=flat-square&logo=supabase&logoColor=white)

Every repo above has a Docker-based local setup and runs CI on every push, with a README that explains scope and tradeoffs rather than just install steps.

## Experience

**2026 → present**
Software Engineer Intern, Hanco Automotive — Jeddah, KSA
Building a luxury car-rental platform end to end — customer-facing site, booking engine, and admin tooling — on Next.js 14, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

**2025 (Jun – Jul)**
Software Engineer Intern, Techvaria — Bangalore, India

## Certifications

`Oracle Agentic AI Foundations` · `Oracle AI Database Foundations` · `OCI AI Foundations` · `AWS Serverless (Demonstrated)`
