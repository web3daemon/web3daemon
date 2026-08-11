<img src="assets/hero.svg" alt="web3daemon — Python Backend / AI Engineer" width="100%">

<img src="assets/status.svg" alt="Open to work — contract or full-time. Stack: Python, FastAPI, asyncio, Pydantic, WebSocket, FastStream, aiogram 3, PostgreSQL, TimescaleDB, SQLAlchemy, Redis, OpenAI, Claude, Grok, OpenRouter, RAG, LangChain, MCP, n8n, TypeScript, React, Next.js, Docker, Linux, Nginx, AWS, GitHub Actions" width="100%">

<img src="assets/rule.svg" alt="" width="100%">

I build Python services that run unattended: exchange pipelines that survive disconnects,
async APIs that respect other people's limits, and LLM systems measured rather than assumed.

Most of the work is commercial and private — trading infrastructure, data platforms and
internal AI services. Clients come back for a second contract. That is the metric I care about.

## What I build

**Market data.** WebSocket collectors write into PostgreSQL / TimescaleDB. Order books are
rebuilt from snapshot and deltas, and gaps are repaired on reconnect.

**Exchanges.** One execution interface behind 11 venues. Each venue gets its own client and
error taxonomy, under shared retry and stream watchdogs.

**Backend.** FastAPI and async SQLAlchemy, SSE with a polling fallback, background workers,
idempotent pipelines.

**AI.** RAG over internal knowledge bases, function calling with structured output, model
routing with fallbacks, and cost accounting per user.

## Two problems that weren't obvious

**Billing that counted silence.**

A platform charged per conversation, and its four-second window started the moment a message
was *fetched* — not when it was answered. So the obvious `poll → llm → reply` loop kept
donating paid conversations to the platform's own auto-responder.

I split polling from processing, and turned the uncovered time into a metric.

**An API with no counter and no cursor.**

Nothing to page by, and an aggressive `429` on top. I wrote a token-bucket client that backs
off honestly on `403`, and reports live progress over SSE — falling back to polling wherever
SSE is blocked.

## Selected work

<table>
<tbody>
  <tr>
    <td width="50%"><a href="https://github.com/web3daemon/zero-block-sniper-reverse-engineering"><img src="assets/repo-zero-block-sniper-reverse-engineering.svg" alt="zero-block-sniper-reverse-engineering" width="100%"></a></td>
    <td width="50%"><a href="https://github.com/web3daemon/file-stats-service"><img src="assets/repo-file-stats-service.svg" alt="file-stats-service" width="100%"></a></td>
  </tr>
  <tr>
    <td width="50%"><a href="https://github.com/web3daemon/vibe-agent-runtime"><img src="assets/repo-vibe-agent-runtime.svg" alt="vibe-agent-runtime" width="100%"></a></td>
    <td width="50%"><a href="https://github.com/web3daemon/kttx-test-task"><img src="assets/repo-kttx-test-task.svg" alt="kttx-test-task" width="100%"></a></td>
  </tr>
  <tr>
    <td width="50%"><a href="https://github.com/web3daemon/polza-test-task"><img src="assets/repo-polza-test-task.svg" alt="polza-test-task" width="100%"></a></td>
    <td width="50%"><a href="https://github.com/web3daemon/tg-ai-assistant"><img src="assets/repo-tg-ai-assistant.svg" alt="tg-ai-assistant" width="100%"></a></td>
  </tr>
  <tr>
    <td width="50%"><a href="https://github.com/web3daemon/bitget"><img src="assets/repo-bitget.svg" alt="bitget" width="100%"></a></td>
    <td width="50%"><a href="https://github.com/web3daemon/proxy6-telegram-bot"><img src="assets/repo-proxy6-telegram-bot.svg" alt="proxy6-telegram-bot" width="100%"></a></td>
  </tr>
</tbody>
</table>

<sub>· <a href="https://github.com/web3daemon?tab=repositories">All repositories</a></sub>

## Contact

<a href="https://t.me/web3daemon"><img src="assets/btn-telegram.svg" alt="Telegram @web3daemon"></a>

Open to backend and AI engineering work — contract or full-time.
