# Consent Policy

## TTL по типам данных

| Тип данных | TTL | Действие по истечении |
|---|---|---|
| Резюме активного кандидата | 6 месяцев | Автоотзыв + Purge |
| Резюме отклоненного кандидата | 3 месяца | Автоотзыв + Purge |
| Scorecard / feedback | 12 месяцев | Anonymize (без PII) |
| Audit-логи | 3 года (152-ФЗ) | Redact PII, сохранить метаданные |
| Векторные эмбеддинги | 3 месяца | Полное удаление |

## Right to be Forgotten
- Отзыв согласия - hard trigger.
- Purge Pipeline SLA < 4 часа.
- Audit Vault: immutable log.