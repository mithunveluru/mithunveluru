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

I build the parts of a product that still have to work after the demo ends — the ingestion job that doesn't choke on a bad file, the endpoint that degrades instead of falling over, the query that's still fast once real data shows up instead of the clean seed data.

B.Tech Computer Science, VIT Vellore, class of 2027. Currently building the booking engine behind a luxury car-rental platform at Hanco Automotive, in Jeddah.

Most of what I've learned about building useful software didn't come from documentation — it came from noticing that the technically cleaner solution and the one someone actually needs aren't always the same thing, and that the gap between them only shows up once you've watched how they actually use what you built. Working on something meant for a market I didn't grow up in has made that harder to ignore: assumptions I'd otherwise never question turn out not to travel. I'd rather build with people who see a problem differently than I do than around them.

---

## At a glance

| | |
|---|---|
| **Building** | Booking engine and admin tooling for a car-rental platform, at Hanco Automotive |
| **Shipped** | FlowSight · ClearClause · Schedora · FileLens |
| **Exploring** | Distributed systems · retrieval · observability |

## Currently trying to understand

What actually happens when a distributed system stops agreeing with itself — replicas drift, a dependency goes quiet, a queue backs up faster than it drains, and latency stops being a single number worth quoting.

How to make a system observable enough that debugging it doesn't come down to reading logs and hoping something looks wrong.

Where hybrid retrieval quietly breaks — the queries neither a vector index nor a keyword index handles well on its own, and why.

## Projects

### FlowSight — behavioral finance platform
`Java · Spring Boot · PostgreSQL · React · Docker`

Categorizing bank and receipt data by hand stops scaling past a handful of accounts, and most tools that promise to help either lock you into their own bank integrations or eventually just hand the work back to you as a spreadsheet.

FlowSight ingests raw transaction and receipt data and turns it into categorized, forecastable spend — 21 analytics modules behind a single API surface. The part worth mentioning isn't the categorization logic; it's that receipt OCR runs as an async job instead of inline with the upload, so someone uploading a receipt isn't stuck waiting on a pipeline that might be slow — and the ingestion endpoint is rate-limited so a burst of uploads can't take the OCR workers down with it. Decoupling the slow part from the request path mattered more than optimizing the slow part itself.

**21 analytics modules · async OCR · rate-limited ingestion**

[View repository ↗](https://github.com/mithunveluru/flowsight)

### ClearClause — AI document intelligence
`Python · FastAPI · Celery · Qdrant · PostgreSQL · Next.js`

Pure semantic search finds documents that mean the same thing; it's bad at finding the exact clause, date, or defined term someone is actually looking for. Pure keyword search has the opposite problem.

ClearClause runs hybrid vector-and-keyword retrieval over legal documents across 26 document types. Ingestion, retrieval, and entity extraction run as separate pipeline stages — entity extraction specifically on its own isolated Celery workers — so a slow extraction job never becomes the reason a search feels slow. Retrieval quality and retrieval latency ended up being a product decision as much as an algorithmic one: the two needed to be able to fail independently of each other.

**26 document types · hybrid retrieval · isolated extraction workers**

[View repository ↗](https://github.com/mithunveluru/clearclause)

### Schedora — AI scheduling platform
`Next.js 14 · Supabase · Google Calendar API · Turborepo`

Most scheduling tools are built for one tenant and get multi-tenancy bolted on afterward, which tends to surface later as one account's data leaking into another's.

Schedora turns natural-language requests into conflict-free calendar events, with OAuth 2.0 authentication and 11 row-level-security policies enforcing tenant isolation at the database layer — not the application layer — across 20 API routes. It ships with 219 passing tests, not because the project demanded it, but because a scheduling tool that's occasionally wrong about a meeting time is worse than one that simply does less.

**11 RLS policies · 20 API routes · 219 tests**

[View live demo ↗](https://schedora-web.vercel.app)

### FileLens — cross-platform file manager
`Rust · Tauri 2 · React 19 · TypeScript · SQLite`

Hashing and comparing a large set of files on a single thread is slow enough that a duplicate-cleanup tool becomes a tool you stop bothering to run.

FileLens is a native desktop app — Rust backend, React frontend over Tauri — built to be fast enough that you'd actually use it. A concurrent detection engine spreads BLAKE3 hashing across an 8-thread worker pool, with native IPC between Rust and the UI so the interface doesn't freeze mid-hash. BLAKE3 over SHA-256 was a deliberate call, for the throughput difference at the volumes this tool runs at.

**8-thread worker pool · BLAKE3 hashing · native IPC**

[View repository ↗](https://github.com/mithunveluru/FileLens)

<details>
<summary><strong>A few of the decisions behind these, distilled</strong></summary>
<br>

- **FlowSight** — decouple the slow part from the request path before you try to optimize the slow part itself.
- **ClearClause** — retrieval and extraction need to be able to fail independently of each other.
- **Schedora** — enforce isolation at the database layer, not the application layer.
- **FileLens** — pick the hash function for the throughput the workload actually needs, not the one everyone defaults to.

</details>

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

Every repo above runs a Docker-based local environment and CI on every push, with a README that explains scope and tradeoffs rather than just setup steps.

## Experience

**2026 → present**
Software Engineer Intern, Hanco Automotive — Jeddah, KSA
Building a luxury car-rental platform end to end — customer-facing site, booking engine, and admin tooling — on Next.js 14, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

**2025 (Jun – Jul)**
Software Engineer Intern, Techvaria — Bangalore, India

## Certifications

`Oracle Agentic AI Foundations` · `Oracle AI Database Foundations` · `OCI AI Foundations` · `AWS Serverless (Demonstrated)`
