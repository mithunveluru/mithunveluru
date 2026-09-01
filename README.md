# Mithun Raghu Veluru

I build the parts of a product that still have to work after the demo ends — the ingestion job that doesn't choke on a bad file, the endpoint that degrades instead of falling over, the query that's still fast once real data shows up instead of the clean seed data.

B.Tech Computer Science, VIT Vellore, class of 2027. Currently building the booking engine behind a luxury car-rental platform at Hanco Automotive, in Jeddah.

[Portfolio](https://mithundev.vercel.app) · [mithunveluru7@gmail.com](mailto:mithunveluru7@gmail.com) · [LinkedIn](https://linkedin.com/in/mithunveluru)

Most of what I've learned about building useful software didn't come from documentation — it came from noticing that the technically cleaner solution and the one someone actually needs aren't always the same thing, and that the gap between them only shows up once you've watched how they actually use what you built. Working on something meant for a market I didn't grow up in has made that harder to ignore: assumptions I'd otherwise never question turn out not to travel. I'd rather build with people who see a problem differently than I do than around them.

## Currently trying to understand

What actually happens when a distributed system stops agreeing with itself — replicas drift, a dependency goes quiet, a queue backs up faster than it drains, and latency stops being a single number worth quoting.

How to make a system observable enough that debugging it doesn't come down to reading logs and hoping something looks wrong.

Where hybrid retrieval quietly breaks — the queries neither a vector index nor a keyword index handles well on its own, and why.

## Projects

### FlowSight — behavioral finance platform
`Java · Spring Boot · PostgreSQL · React · Docker`

Categorizing bank and receipt data by hand stops scaling past a handful of accounts, and most tools that promise to help either lock you into their own bank integrations or eventually just hand the work back to you as a spreadsheet.

FlowSight ingests raw transaction and receipt data and turns it into categorized, forecastable spend — 21 analytics modules behind a single API surface. The part worth mentioning isn't the categorization logic; it's that receipt OCR runs as an async job instead of inline with the upload, so someone uploading a receipt isn't stuck waiting on a pipeline that might be slow — and the ingestion endpoint is rate-limited so a burst of uploads can't take the OCR workers down with it. Decoupling the slow part from the request path mattered more than optimizing the slow part itself.

[Repository](https://github.com/mithunveluru/flowsight)

### ClearClause — AI document intelligence
`Python · FastAPI · Celery · Qdrant · PostgreSQL · Next.js`

Pure semantic search finds documents that mean the same thing; it's bad at finding the exact clause, date, or defined term someone is actually looking for. Pure keyword search has the opposite problem.

ClearClause runs hybrid vector-and-keyword retrieval over legal documents across 26 document types. Ingestion, retrieval, and entity extraction run as separate pipeline stages — entity extraction specifically on its own isolated Celery workers — so a slow extraction job never becomes the reason a search feels slow. Retrieval quality and retrieval latency ended up being a product decision as much as an algorithmic one: the two needed to be able to fail independently of each other.

[Repository](https://github.com/mithunveluru/clearclause)

### Schedora — AI scheduling platform
`Next.js 14 · Supabase · Google Calendar API · Turborepo`

Most scheduling tools are built for one tenant and get multi-tenancy bolted on afterward, which tends to surface later as one account's data leaking into another's.

Schedora turns natural-language requests into conflict-free calendar events, with OAuth 2.0 authentication and 11 row-level-security policies enforcing tenant isolation at the database layer — not the application layer — across 20 API routes. It ships with 219 passing tests, not because the project demanded it, but because a scheduling tool that's occasionally wrong about a meeting time is worse than one that simply does less.

[Live demo](https://schedora-web.vercel.app)

### FileLens — cross-platform file manager
`Rust · Tauri 2 · React 19 · TypeScript · SQLite`

Hashing and comparing a large set of files on a single thread is slow enough that a duplicate-cleanup tool becomes a tool you stop bothering to run.

FileLens is a native desktop app — Rust backend, React frontend over Tauri — built to be fast enough that you'd actually use it. A concurrent detection engine spreads BLAKE3 hashing across an 8-thread worker pool, with native IPC between Rust and the UI so the interface doesn't freeze mid-hash. BLAKE3 over SHA-256 was a deliberate call, for the throughput difference at the volumes this tool runs at.

[Repository](https://github.com/mithunveluru/FileLens)

More detail on each at [mithundev.vercel.app](https://mithundev.vercel.app).

## Stack

**Languages** — Python, Java, TypeScript, C++, Rust, SQL
**Backend** — FastAPI, Spring Boot, Flask, Celery
**Frontend** — React, Next.js, Tauri
**AI / Data** — PyTorch, TensorFlow, scikit-learn, Pandas, Qdrant
**Storage** — PostgreSQL, MySQL, MongoDB, Redis, SQLite
**Infra** — Docker, GitHub Actions, AWS, Vercel, Supabase

Every repo above runs a Docker-based local environment and CI on every push, with a README that explains scope and tradeoffs rather than just setup steps.

## Experience

**Hanco Automotive** — Jeddah, KSA · Software Engineer Intern · May 2026 – present
Building a luxury car-rental platform end to end — customer-facing site, booking engine, and admin tooling — on Next.js 14, TypeScript, and Supabase, deployed on Vercel behind Cloudflare.

**Techvaria** — Bangalore, India · Software Engineer Intern · Jun – Jul 2025

## Certifications

Oracle Agentic AI Foundations · OCI AI Foundations · Oracle AI Database Foundations · AWS Serverless (Demonstrated)
