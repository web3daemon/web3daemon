<h1 align="center">Backend engineer — real-time systems &amp; AI products</h1>

<p align="center">
  Python services that run unattended: exchange pipelines that survive disconnects,<br>
  async APIs that respect other people's limits, LLM systems measured rather than assumed.
</p>

<p align="center">
  <a href="https://t.me/web3daemon"><img src="https://img.shields.io/badge/Telegram-%40web3daemon-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram @web3daemon"></a>
  <img src="https://img.shields.io/badge/Available-contract%20%2F%20full--time-2ea44f?style=flat-square" alt="Available for contract or full-time">
</p>

---

Most of my work is commercial and private — trading infrastructure, data platforms
and internal AI services built for clients. Clients come back for a second contract.
That is the metric I care about.

## ⚡ What I build

**📊 Market data in real time**
WebSocket collectors writing into PostgreSQL / TimescaleDB. Order book reconstructed
from snapshot and deltas with continuity control, reconnect and rebuild on gaps,
candle aggregates built by the database itself.

**🔌 Exchange integration at scale**
A single execution interface behind 11 venues — per-exchange WebSocket clients and
error taxonomies, shared retry and stream-health watchdogs. The next exchange is a
module, not a rewrite.

**🧩 Backend and APIs**
FastAPI, async SQLAlchemy, SSE with polling fallback, JWT, background workers,
idempotent pipelines with multi-level deduplication. Docker, CI, tests as a default,
not a favour.

**🧠 AI systems**
RAG over internal knowledge bases, agents with function calling and structured
output, model routing with fallbacks, conversation memory, cost accounting per user.

## 🛠 Problems I've solved

**A blind, rate-limited external API.** No total count, no cursor, aggressive `429`.
Built a token-bucket client with retries, honest `403` cooldown, and live progress
over SSE that silently falls back to polling where SSE is blocked.

**An agent platform that charged for silence.** Its 4-second window counted to the
moment a message was *fetched*, not answered — so the obvious `poll → llm → reply`
loop handed paid conversations to the platform's own responder. Separated polling
from processing and exposed the uncovered time as a metric, turning an invisible
cost into an alert.

**Imports that could not be trusted twice.** Multi-level deduplication and validation
across two sources, idempotent by construction: re-running the pipeline changes
nothing, and every anomaly in the source data is documented rather than silently
dropped.

## 💻 Stack

**Core**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![asyncio](https://img.shields.io/badge/asyncio-3776AB?style=flat-square)
![WebSocket](https://img.shields.io/badge/WebSocket-4353FF?style=flat-square)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)

**Data**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![TimescaleDB](https://img.shields.io/badge/TimescaleDB-FDB515?style=flat-square&logo=timescale&logoColor=black)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)

**AI**

![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![Claude](https://img.shields.io/badge/Claude-D97757?style=flat-square&logo=anthropic&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![RAG](https://img.shields.io/badge/RAG-000000?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-000000?style=flat-square)
![n8n](https://img.shields.io/badge/n8n-EA4B71?style=flat-square&logo=n8n&logoColor=white)

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

<br>

<details>
<summary><b>🇷🇺 Русская версия</b></summary>

<br>

# Backend-инженер — системы реального времени и AI-продукты

Пишу на Python сервисы, которые работают без присмотра: биржевые пайплайны,
переживающие разрывы связи, асинхронные API, уважающие чужие лимиты, и LLM-системы,
качество которых измеряется, а не предполагается.

Большая часть работы коммерческая и закрытая — торговая инфраструктура, платформы
данных и внутренние AI-сервисы под заказчика. Заказчики возвращаются за вторым
контрактом. Это та метрика, которая меня интересует.

## ⚡ Что делаю

**📊 Рыночные данные в реальном времени**
WebSocket-коллекторы с записью в PostgreSQL / TimescaleDB. Стакан реконструируется
из снапшота и дельт с контролем непрерывности, при разрыве — переподключение и
пересборка, свечные агрегаты строит сама база.

**🔌 Интеграция с биржами**
Единый интерфейс исполнения поверх 11 площадок — свой WebSocket-клиент и своя
таксономия ошибок на каждую биржу, общий retry и watchdog состояния стрима.
Следующая биржа — это новый модуль, а не переписывание.

**🧩 Backend и API**
FastAPI, асинхронный SQLAlchemy, SSE с фолбэком на polling, JWT, фоновые воркеры,
идемпотентные пайплайны с многоуровневой дедупликацией. Docker, CI и тесты — норма,
а не одолжение.

**🧠 AI-системы**
RAG по внутренним базам знаний, агенты с function calling и structured output,
маршрутизация моделей с fallback, память диалога, учёт стоимости по пользователям.

## 🛠 Задачи, которые решал

**Внешнее API, работающее вслепую и под лимитом.** Ни общего количества, ни курсора,
жёсткие `429`. Сделал клиент с token-bucket, повторами, честным простоем по `403` и
живым прогрессом через SSE, который незаметно переходит на polling там, где SSE
заблокирован.

**Платформа агентов, бравшая деньги за молчание.** Её четырёхсекундное окно
отсчитывалось до момента, когда сообщение *забрали*, а не ответили на него — поэтому
очевидный цикл `poll → llm → reply` отдавал платные диалоги встроенному
авто-ответчику. Разделил опрос и обработку, а непокрытое время вывел в метрику,
превратив невидимые расходы в алерт.

**Импорт, которому нельзя доверять дважды.** Многоуровневая дедупликация и валидация
по двум источникам, идемпотентность по построению: повторный запуск ничего не меняет,
а каждая аномалия в исходных данных задокументирована, а не отброшена молча.

## 💻 Стек

Python · FastAPI · asyncio · WebSocket · Pydantic
PostgreSQL · TimescaleDB · SQLAlchemy · Redis
OpenAI · Claude · Gemini · RAG · векторный поиск · LangChain · MCP · n8n
Docker · Linux · Nginx · AWS · GitHub Actions

Открыт к backend- и AI-задачам — контракт или полная занятость.
Telegram: [@web3daemon](https://t.me/web3daemon)

</details>

<br>

<p align="center">
  <sub>Open to backend and AI engineering work — contract or full-time.</sub>
</p>
