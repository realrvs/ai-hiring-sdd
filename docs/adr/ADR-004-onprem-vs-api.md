# ADR-004: On-prem GigaChat 3.5 Ultra vs API

## Статус
Accepted

## Контекст
Выбор между on-prem GPU-кластером и GigaChat API:
- On-prem: CAPEX + OPEX, data residency.
- API: 0 CAPEX, ~650 руб/1M токенов (Max).

## Решение
Гибридная модель:
- База - on-prem GigaChat 3.5 Ultra (при утилизации GPU >60% и объеме >500M токенов/мес).
- Пики - через API.
- Edge-задачи - GigaChat 3 Lightning.

## Последствия
Плюсы:
- Data residency для PII.
- Экономия при высокой утилизации.
- Гибкость для пиков.

Минусы:
- Сложность гибридного управления.
- Требуются MLOps-кадры.