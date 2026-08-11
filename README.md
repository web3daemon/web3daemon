<img src="assets/hero.svg" alt="web3daemon — Python Backend / AI Engineer" width="100%">

<p align="center">
  <b>English</b>&nbsp; ·&nbsp; <a href="#russian">Русский</a>&nbsp; ·&nbsp; <a href="https://t.me/web3daemon">Telegram</a>
</p>

<img src="assets/rule.svg" alt="" width="100%">

### Python Backend / AI Engineer

Services that run unattended: exchange pipelines that survive disconnects, async APIs that
respect other people's limits, LLM systems measured rather than assumed.

Most of my work is commercial and private — trading infrastructure, data platforms and
internal AI services built for clients. Clients come back for a second contract. That is the
metric I care about.

## What I build

**Market data in real time**<br>
WebSocket collectors writing into PostgreSQL / TimescaleDB. Order book reconstructed from
snapshot and deltas with continuity control, reconnect and rebuild on gaps, candle aggregates
built by the database itself.

**Exchange integration at scale**<br>
A single execution interface behind 11 venues — per-exchange WebSocket clients and error
taxonomies, shared retry and stream-health watchdogs. The next exchange is a module, not a
rewrite.

**Backend and APIs**<br>
FastAPI, async SQLAlchemy, SSE with polling fallback, JWT, background workers, idempotent
pipelines with multi-level deduplication. Docker, CI, tests as a default, not a favour.

**AI systems**<br>
RAG over internal knowledge bases, agents with function calling and structured output, model
routing with fallbacks, conversation memory, cost accounting per user.

## Problems I've solved

**A blind, rate-limited external API.**<br>
No total count, no cursor, aggressive `429`. Built a token-bucket client with retries, honest
`403` cooldown, and live progress over SSE that silently falls back to polling where SSE is
blocked.

**An agent platform that charged for silence.**<br>
Its 4-second window counted to the moment a message was *fetched*, not answered — so the
obvious `poll → llm → reply` loop handed paid conversations to the platform's own responder.
Separated polling from processing and exposed the uncovered time as a metric, turning an
invisible cost into an alert.

**Imports that could not be trusted twice.**<br>
Multi-level deduplication and validation across two sources, idempotent by construction:
re-running the pipeline changes nothing, and every anomaly in the source data is documented
rather than silently dropped.

## Selected work

| Project | Stack | What it is |
| :-- | :-- | :-- |
| **[zero-block-sniper-reverse-engineering](https://github.com/web3daemon/zero-block-sniper-reverse-engineering)** | Python | Reverse-engineering a zero-block pump.fun sniper on Solana: behavioural analysis, an interpretable selection model, and a replica strategy with an honest backtest. |
| **[file-stats-service](https://github.com/web3daemon/file-stats-service)** | Python · React | Downloads a blindly paginated, rate-limited file catalogue and reports digit statistics. Token-bucket client with `429` / `403` handling, SSE progress with polling fallback, Docker, CI. |
| **[vibe-agent-runtime](https://github.com/web3daemon/vibe-agent-runtime)** | Python | Agent runtime that never leaves a poll unparked — polling separated from processing so the platform's paid auto-responder never fires. Ships six findings on the Agent API. |
| **[kttx-test-task](https://github.com/web3daemon/kttx-test-task)** | Python | Asynchronous payment processing: FastAPI writes the payment and its event in one transaction (transactional outbox), a FastStream consumer delivers signed webhooks with TTL-queue retries and a DLQ. |
| **[polza-test-task](https://github.com/web3daemon/polza-test-task)** | TypeScript | JSON + CSV to PostgreSQL with three-level deduplication, validation and idempotent re-runs, three analytical queries, and a `/companies` page on Next.js App Router. |
| **[tg-ai-assistant](https://github.com/web3daemon/tg-ai-assistant)** | Python | Private Telegram AI assistant on aiogram 3 and OpenRouter: text, documents, images and voice, background queue for heavy media, rolling memory, model routing with fallbacks. |
| **[bitget](https://github.com/web3daemon/bitget)** | Python | Minimal wrapper for the Bitget V2 USDT-M futures API — HMAC request signing, account, positions, orders and TP/SL, defaulting to demo trading. |
| **[proxy6-telegram-bot](https://github.com/web3daemon/proxy6-telegram-bot)** | Python | aiogram 3 bot for managing proxy servers on PROXY6. |

<sub>· <a href="https://github.com/web3daemon?tab=repositories">All repositories</a></sub>

## Stack

| | |
| :-- | :-- |
| **Core** | Python · FastAPI · asyncio · Pydantic · WebSocket · FastStream · aiogram 3 |
| **Data** | PostgreSQL · TimescaleDB · SQLAlchemy · Redis |
| **AI** | OpenAI · Claude · Grok · OpenRouter · RAG · LangChain · MCP · n8n |
| **Web** | TypeScript · React · Next.js |
| **Infrastructure** | Docker · Linux · Nginx · AWS · GitHub Actions |

## Contact

<a href="https://t.me/web3daemon"><img src="assets/btn-telegram.svg" alt="Telegram @web3daemon"></a>

Open to backend and AI engineering work — contract or full-time.

<img src="assets/rule.svg" alt="" width="100%">

<a name="russian"></a>

<details>
<summary><b>Русская версия</b></summary>

<br>

### Python Backend / AI Engineer

Сервисы, которые работают без присмотра: биржевые пайплайны, переживающие разрывы связи,
асинхронные API, уважающие чужие лимиты, и LLM-системы, качество которых измеряется,
а не предполагается.

Большая часть работы коммерческая и закрытая — торговая инфраструктура, платформы данных
и внутренние AI-сервисы под заказчика. Заказчики возвращаются за вторым контрактом.
Это та метрика, которая меня интересует.

## Что делаю

**Рыночные данные в реальном времени**<br>
WebSocket-коллекторы с записью в PostgreSQL / TimescaleDB. Стакан реконструируется из
снапшота и дельт с контролем непрерывности, при разрыве — переподключение и пересборка,
свечные агрегаты строит сама база.

**Интеграция с биржами**<br>
Единый интерфейс исполнения поверх 11 площадок — свой WebSocket-клиент и своя таксономия
ошибок на каждую биржу, общий retry и watchdog состояния стрима. Следующая биржа — это
новый модуль, а не переписывание.

**Backend и API**<br>
FastAPI, асинхронный SQLAlchemy, SSE с фолбэком на polling, JWT, фоновые воркеры,
идемпотентные пайплайны с многоуровневой дедупликацией. Docker, CI и тесты — норма,
а не одолжение.

**AI-системы**<br>
RAG по внутренним базам знаний, агенты с function calling и structured output, маршрутизация
моделей с fallback, память диалога, учёт стоимости по пользователям.

## Задачи, которые решал

**Внешнее API, работающее вслепую и под лимитом.**<br>
Ни общего количества, ни курсора, жёсткие `429`. Сделал клиент с token-bucket, повторами,
честным простоем по `403` и живым прогрессом через SSE, который незаметно переходит на
polling там, где SSE заблокирован.

**Платформа агентов, бравшая деньги за молчание.**<br>
Её четырёхсекундное окно отсчитывалось до момента, когда сообщение *забрали*, а не ответили
на него — поэтому очевидный цикл `poll → llm → reply` отдавал платные диалоги встроенному
авто-ответчику. Разделил опрос и обработку, а непокрытое время вывел в метрику, превратив
невидимые расходы в алерт.

**Импорт, которому нельзя доверять дважды.**<br>
Многоуровневая дедупликация и валидация по двум источникам, идемпотентность по построению:
повторный запуск ничего не меняет, а каждая аномалия в исходных данных задокументирована,
а не отброшена молча.

## Избранные проекты

| Проект | Стек | Что это |
| :-- | :-- | :-- |
| **[zero-block-sniper-reverse-engineering](https://github.com/web3daemon/zero-block-sniper-reverse-engineering)** | Python | Реверс-инжиниринг zero-block снайпера pump.fun на Solana: поведенческий анализ, интерпретируемая модель отбора и стратегия-реплика с честным бэктестом. |
| **[file-stats-service](https://github.com/web3daemon/file-stats-service)** | Python · React | Скачивает вслепую пагинированный каталог файлов под рейт-лимитом и считает статистику цифр. Клиент с token-bucket и обработкой `429` / `403`, прогресс по SSE с фолбэком на polling, Docker, CI. |
| **[vibe-agent-runtime](https://github.com/web3daemon/vibe-agent-runtime)** | Python | Рантайм агента, не оставляющий опрос без обработки — опрос отделён от обработки, поэтому платный авто-ответчик платформы не срабатывает. Плюс шесть находок по Agent API. |
| **[kttx-test-task](https://github.com/web3daemon/kttx-test-task)** | Python | Асинхронная обработка платежей: FastAPI пишет платёж и событие в одной транзакции (transactional outbox), консьюмер на FastStream доставляет подписанные вебхуки с ретраями через TTL-очередь и DLQ. |
| **[polza-test-task](https://github.com/web3daemon/polza-test-task)** | TypeScript | JSON + CSV в PostgreSQL с трёхуровневой дедупликацией, валидацией и идемпотентными перезапусками, три аналитических запроса и страница `/companies` на Next.js App Router. |
| **[tg-ai-assistant](https://github.com/web3daemon/tg-ai-assistant)** | Python | Приватный Telegram AI-ассистент на aiogram 3 и OpenRouter: текст, документы, изображения и голос, фоновая очередь для тяжёлой медиа, скользящая память, маршрутизация моделей с fallback. |
| **[bitget](https://github.com/web3daemon/bitget)** | Python | Минимальная обёртка над Bitget V2 USDT-M futures API — подпись запросов HMAC, аккаунт, позиции, ордера и TP/SL, по умолчанию demo trading. |
| **[proxy6-telegram-bot](https://github.com/web3daemon/proxy6-telegram-bot)** | Python | Бот на aiogram 3 для управления прокси-серверами на PROXY6. |

<sub>· <a href="https://github.com/web3daemon?tab=repositories">Все репозитории</a></sub>

## Стек

| | |
| :-- | :-- |
| **Основное** | Python · FastAPI · asyncio · Pydantic · WebSocket · FastStream · aiogram 3 |
| **Данные** | PostgreSQL · TimescaleDB · SQLAlchemy · Redis |
| **AI** | OpenAI · Claude · Grok · OpenRouter · RAG · LangChain · MCP · n8n |
| **Web** | TypeScript · React · Next.js |
| **Инфраструктура** | Docker · Linux · Nginx · AWS · GitHub Actions |

## Контакты

<a href="https://t.me/web3daemon"><img src="assets/btn-telegram.svg" alt="Telegram @web3daemon"></a>

Открыт к backend- и AI-задачам — контракт или полная занятость.

</details>
