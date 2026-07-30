**English** · [Русский](README.ru.md)

# Backend engineer — real-time systems and AI products

I build Python services that run unattended: exchange data pipelines that survive
disconnects, async APIs that respect other people's limits, and LLM products that
are measured rather than assumed. Most of my work is commercial and private.
Clients come back for a second contract — that is the metric I care about.

### What I build

**Market data in real time** — WebSocket collectors writing into PostgreSQL /
TimescaleDB: order book reconstructed from snapshot and deltas with continuity
control, reconnect and rebuild on gaps, candle aggregates built by the database.

**Exchange integration at scale** — a single execution interface behind 11 venues.
Per-exchange WebSocket clients and error taxonomies, shared retry and stream-health
watchdogs. The next exchange is a module, not a rewrite.

**Backend and APIs** — FastAPI, async SQLAlchemy, SSE with polling fallback, JWT,
background workers, idempotent pipelines with multi-level deduplication, Docker,
CI, tests.

**AI systems** — RAG over internal knowledge bases, agents with function calling
and structured output, model routing with fallbacks, conversation memory, cost
accounting per user.

### Stack

`Python` `asyncio` `FastAPI` `aiohttp` `WebSocket` `PostgreSQL` `TimescaleDB`
`SQLAlchemy` `Redis` `Docker` `Linux` `Nginx` `AWS`

`OpenAI` `Claude` `Gemini` `RAG` `vector search` `LangChain` `MCP` `n8n` `aiogram`

---

Open to backend and AI engineering work — contract or full-time.
