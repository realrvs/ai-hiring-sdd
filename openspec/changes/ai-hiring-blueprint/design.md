## Context

Blueprint — корпоративный стандарт AI-driven найма в enterprise-контуре с требованиями 152-ФЗ, on-prem размещения PII и импортозамещения LLM.

## Goals / Non-Goals

**Goals:**
- Снизить Time-to-Hire на 30–40% и Cost per Hire до < 0.7x.
- Обеспечить 152-ФЗ compliance через Two-Way Masking и Consent Layer.
- Внедрить контролируемое использование LLM с бюджетом и fallback.

**Non-Goals:**
- Полный отказ от человека на этапе оффера.
- Использование внешних облачных LLM для PII.

## Decisions

### Компонентная архитектура

Слои (сверху вниз): HR LLM Gateway → Recruitment Agent Platform → Candidate Context Provider (MCP) → Artifact Store (Gitea) → Consent & Retention Layer → Anonymization Tokenizer.

### Latency-классы агентов

| Параметр | Фоновый | Интерактивный |
|---|---|---|
| Задачи | Скрининг, ранжирование, JD | Чат-бот, FAQ, scheduling |
| Latency p95 | 15 мин | 5 сек |
| Модель | GigaChat 3.5 Ultra | GigaChat 3 Lightning |
| Бюджет | 1.0 CU / батч | 0.02 CU |

### Поток Screening (batch)

Резюме (PII) → Pre-commit hook PII-детектор → Gitea Actions (Semgrep PII, Block) → Anonymization Tokenizer → LLM Gateway → GigaChat 3 Lightning → Scorecard + риски → Re-identification в UI → Self-Check Report.

### Поток Consent Revocation

Кандидат отзывает согласие → Consent API (мгновенно) → Метка consent-revoked (<5 мин) → Circuit Breaker → Purge Pipeline (<1 час) → Git force-push + git filter-repo (<2 ч), Vector Index (<2 ч), MCP Logs (<4 ч) → Audit Vault (<4 ч).

### Технологический стек

| Слой | Технология |
|---|---|
| LLM (фон) | GigaChat 3.5 Ultra (on-prem, 432B MoE) |
| LLM (интерактив) | GigaChat 3 Lightning |
| LLM (локальный) | Qwen / DeepSeek через Ollama |
| Gateway | KodikRouter / LiteLLM |
| Artifact Store | Gitea / GitLab On-premise |
| CI/CD | Gitea Actions |
| PII Scan | Semgrep (Block) |
| Token Vault | On-prem, AES-256 |
| Vector DB | RAG-индекс (3 мес TTL) |
| MCP | MCP-сервер для Gitea/Forgejo |
| Контейнеризация | Docker |

## Risks / Trade-offs

- **Риск галлюцинаций** → Self-Check Report обязателен на каждом этапе.
- **Риск bias** → Diff-based Bias Detection асинхронно.
- **Риск утечки PII** → Token Vault on-prem, RBAC, аудит демаскирований.
- **Trade-off:** гибридная модель on-prem + API усложняет управление, но даёт data residency и гибкость.

## Migration Plan

1. Фаза 0: инфраструктура (Gitea, Gateway, Tokenizer).
2. Фаза 1: Assist (Human-in-the-Loop).
3. Фаза 2: Augment (Human-on-the-Loop).
4. Фаза 3: Autonomous (Human-out-of-the-Loop).

## Open Questions

- Точные пороги GPU-утилизации для переключения on-prem ↔ API.
- Формат Self-Check Report для разных типов агентов.
