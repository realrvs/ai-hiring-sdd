## ADDED Requirements

### Requirement: Многоуровневый Fallback

Система SHALL переключать уровни: Ур.1 (GigaChat 3.5 Ultra) → Ур.2 (Lightning) → Ур.3 (Human).

#### Scenario: Переключение на Ур.2

- **WHEN** error rate > 5% ИЛИ latency > 30s ИЛИ GPU util > 90%
- **THEN** система переключается на Ур.2

#### Scenario: Переключение на Ур.3

- **WHEN** error rate > 10% ИЛИ latency > 60s
- **THEN** система переключается на Ур.3 (Human)

### Requirement: Circuit Breaker

Система SHALL открывать Circuit Breaker после 15 минут недоступности и закрывать через 5 минут после восстановления.

#### Scenario: Открытие Circuit Breaker

- **WHEN** недоступность длится более 15 минут
- **THEN** Circuit Breaker открывается

#### Scenario: Закрытие Circuit Breaker

- **WHEN** восстановление подтверждено и прошло 5 минут
- **THEN** Circuit Breaker закрывается
