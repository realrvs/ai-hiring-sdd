## ADDED Requirements

### Requirement: Consent Revocation как hard trigger

Система SHALL немедленно останавливать пайплайны при отзыве согласия.

#### Scenario: Отзыв согласия

- **WHEN** кандидат отзывает согласие
- **THEN** система мгновенно останавливает все пайплайны и помечает артефакты `consent-revoked`

### Requirement: Purge Pipeline

Система SHALL очищать Git, Vector Index и MCP Logs со SLA < 4 часа.

#### Scenario: Выполнение Purge

- **WHEN** consent-revoked зафиксирован
- **THEN** система выполняет Purge Pipeline за < 4 часа и записывает результат в Audit Vault

### Requirement: TTL по типам данных

Система SHALL применять TTL: резюме активного кандидата 6 мес, отклонённого 3 мес, scorecard 12 мес, audit 3 года, векторные эмбеддинги 3 мес.

#### Scenario: Истечение TTL

- **WHEN** TTL истекает
- **THEN** система выполняет действие по типу данных: автоотзыв + Purge, Anonymize или Redact PII

### Requirement: Consent coverage

Система SHALL обеспечивать 100% consent coverage для активных кандидатов.

#### Scenario: Проверка coverage

- **WHEN** кандидат активен
- **THEN** система проверяет наличие активного согласия
