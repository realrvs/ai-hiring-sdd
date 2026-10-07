# ADR-005: Consent Revocation как hard trigger

## Статус
Accepted

## Контекст
Отзыв согласия кандидатом:
- Мягкий сигнал -> риск нарушения 152-ФЗ.
- Нужна немедленная реакция.

## Решение
Hard trigger:
- Consent API -> мгновенно.
- Метка consent-revoked -> <5 мин.
- Circuit Breaker: остановка всех пайплайнов.
- Purge Pipeline: SLA <4 часа.

## Последствия
Плюсы:
- 152-ФЗ compliance.
- Right to be Forgotten реализован.
- Audit trail.

Минусы:
- Возможны ложные отзывы.
- Требуется верификация личности кандидата.