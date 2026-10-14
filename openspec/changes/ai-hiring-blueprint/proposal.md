## Why

Корпоративный найм в enterprise-контуре сталкивается с высоким Cost per Hire (120 000 руб на вакансию), длинным Time-to-Hire (3+ недели), рисками утечки PII (152-ФЗ, GDPR Art. 17), неконтролируемым использованием LLM (галлюцинации, дискриминация) и отсутствием метрик качества найма.

## What Changes

- Внедряется Blueprint — корпоративный стандарт AI-driven найма через три фазы зрелости: Assist (Human-in-the-Loop), Augment (Human-on-the-Loop), Autonomous (Human-out-of-the-Loop).
- Добавляется HR LLM Gateway с Two-Way Masking, budget enforcement и compliance-контролем.
- Добавляется Recruitment Agent Platform с изолированными песочницами и интеграцией ATS/HRIS.
- Добавляется Candidate Context Provider (MCP) для инкрементального обогащения контекста.
- Добавляется Artifact Store (Gitea) с Docs-as-Code, CI/CD и PII Scan.
- Добавляется Consent & Retention Layer с TTL, Purge Pipeline и Right to be Forgotten.
- Добавляется Anonymization Tokenizer с Token Vault (AES-256) и RBAC.
- Добавляется Diff-based Bias Detection и Self-Check Report на каждом этапе.

## Impact

- Затронутые capabilities: maturity-phases, hiring-pipeline, budget-enforcement, fallback-chain, bias-detection, two-way-masking, consent-retention.
- Затронутые команды: HRD, DPO, MLOps, ИБ, Архитектурный совет.
- Целевые метрики: Time-to-Hire −30–40%, Cost per Hire < 0.7x, Fairness > 85%, PII-инциденты 0, Purge SLA < 4 часа.
