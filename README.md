<img src="assets/hero.svg" alt="web3daemon — Python Backend / AI Engineer" width="100%">

<p align="center">
  <b>English</b>&nbsp; ·&nbsp; <a href="#russian">Русский</a>&nbsp; ·&nbsp; <a href="https://t.me/web3daemon">Telegram</a>
</p>

<img src="assets/status.svg" alt="Open to work — contract or full-time. Stack: Python, FastAPI, asyncio, Pydantic, WebSocket, FastStream, aiogram 3, PostgreSQL, TimescaleDB, SQLAlchemy, Redis, OpenAI, Claude, Grok, OpenRouter, RAG, LangChain, MCP, n8n, TypeScript, React, Next.js, Docker, Linux, Nginx, AWS, GitHub Actions" width="100%">

<img src="assets/rule.svg" alt="" width="100%">

I build Python services that run unattended: exchange pipelines that survive disconnects,
async APIs that respect other people's limits, LLM systems measured rather than assumed.

Most of the work is commercial and private — trading infrastructure, data platforms, internal
AI services. Clients come back for a second contract. That is the metric I care about.

## What I build

**Market data** — WebSocket collectors into PostgreSQL / TimescaleDB, order books rebuilt from
snapshot and deltas, gaps repaired on reconnect.

**Exchanges** — one execution interface behind 11 venues, per-venue error taxonomies under
shared retry and watchdogs.

**Backend** — FastAPI, async SQLAlchemy, SSE with polling fallback, background workers,
idempotent pipelines.

**AI** — RAG over internal knowledge bases, function calling with structured output, model
routing with fallbacks, per-user cost accounting.

## Two problems that weren't obvious

**Billing that counted silence.**<br>
A platform's four-second window started when a message was *fetched*, not answered — so the
obvious `poll → llm → reply` loop was donating paid conversations to its own auto-responder.
I split polling from processing and turned the uncovered time into a metric.

**An API with no counter and no cursor.**<br>
Nothing to page by, aggressive `429`. Token-bucket client with honest `403` cooldown, and live
progress over SSE that falls back to polling where SSE is blocked.

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

<img src="assets/rule.svg" alt="" width="100%">

<a name="russian"></a>

<details>
<summary><b>Русская версия</b></summary>

<br>

Пишу на Python сервисы, которые работают без присмотра: биржевые пайплайны, переживающие
разрывы связи, асинхронные API, уважающие чужие лимиты, и LLM-системы, качество которых
измеряется, а не предполагается.

Большая часть работы коммерческая и закрытая — торговая инфраструктура, платформы данных,
внутренние AI-сервисы. Заказчики возвращаются за вторым контрактом. Это та метрика, которая
меня интересует.

## Что делаю

**Рыночные данные** — WebSocket-коллекторы в PostgreSQL / TimescaleDB, стакан собирается из
снапшота и дельт, разрывы чинятся переподключением.

**Биржи** — единый интерфейс исполнения поверх 11 площадок, своя таксономия ошибок на каждую
под общим retry и watchdog.

**Backend** — FastAPI, асинхронный SQLAlchemy, SSE с фолбэком на polling, фоновые воркеры,
идемпотентные пайплайны.

**AI** — RAG по внутренним базам знаний, function calling со структурированным выводом,
маршрутизация моделей с fallback, учёт стоимости по пользователям.

## Две неочевидные задачи

**Тарификация, которая считала молчание.**<br>
Четырёхсекундное окно платформы начиналось в момент, когда сообщение *забрали*, а не когда
ответили — поэтому очевидный цикл `poll → llm → reply` дарил платные диалоги её собственному
авто-ответчику. Разделил опрос и обработку, непокрытое время вывел в метрику.

**API без счётчика и без курсора.**<br>
Пагинировать не по чему, жёсткие `429`. Клиент с token-bucket и честным простоем по `403`,
живой прогресс через SSE с переходом на polling там, где SSE заблокирован.

## Избранные проекты

| Проект | Стек | Что это |
| :-- | :-- | :-- |
| **[zero-block-sniper-reverse-engineering](https://github.com/web3daemon/zero-block-sniper-reverse-engineering)** | Python | Реверс-инжиниринг zero-block снайпера pump.fun на Solana: поведенческий анализ, интерпретируемая модель отбора, стратегия-реплика с честным бэктестом. |
| **[file-stats-service](https://github.com/web3daemon/file-stats-service)** | Python · React | Слепо пагинированный каталог под рейт-лимитом: token-bucket, обработка `429` / `403`, прогресс по SSE с фолбэком на polling. |
| **[vibe-agent-runtime](https://github.com/web3daemon/vibe-agent-runtime)** | Python | Рантайм агента: опрос отделён от обработки, поэтому платный авто-ответчик платформы не срабатывает. Плюс шесть находок по Agent API. |
| **[kttx-test-task](https://github.com/web3daemon/kttx-test-task)** | Python | Асинхронные платежи: transactional outbox в одной транзакции, консьюмер на FastStream, подписанные вебхуки с ретраями через TTL-очередь и DLQ. |
| **[polza-test-task](https://github.com/web3daemon/polza-test-task)** | TypeScript | JSON + CSV в PostgreSQL с трёхуровневой дедупликацией и идемпотентными перезапусками, три аналитических запроса, страница на Next.js. |
| **[tg-ai-assistant](https://github.com/web3daemon/tg-ai-assistant)** | Python | Telegram AI-ассистент на aiogram 3 и OpenRouter: текст, документы, изображения и голос, фоновая очередь, скользящая память, маршрутизация моделей. |
| **[bitget](https://github.com/web3daemon/bitget)** | Python | Обёртка над Bitget V2 USDT-M futures API — подпись HMAC, аккаунт, позиции, ордера и TP/SL, по умолчанию demo trading. |
| **[proxy6-telegram-bot](https://github.com/web3daemon/proxy6-telegram-bot)** | Python | Бот на aiogram 3 для управления прокси-серверами на PROXY6. |

<sub>· <a href="https://github.com/web3daemon?tab=repositories">Все репозитории</a></sub>

## Контакты

<a href="https://t.me/web3daemon"><img src="assets/btn-telegram.svg" alt="Telegram @web3daemon"></a>

Открыт к backend- и AI-задачам — контракт или полная занятость.

</details>
