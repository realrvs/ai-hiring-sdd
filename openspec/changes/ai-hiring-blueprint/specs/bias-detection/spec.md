## ADDED Requirements

### Requirement: Diff-based Bias Detection

Система SHALL запускать Bias Detection асинхронно после каждого этапа только для изменённых решений.

#### Scenario: Асинхронный запуск

- **WHEN** этап завершён
- **THEN** система асинхронно запускает Bias Detection по diff

#### Scenario: Fairness score ниже порога на diff

- **WHEN** fairness score изменённых решений < 85%
- **THEN** система ставит метку `bias-risk`

#### Scenario: Накопленный fairness score ниже порога

- **WHEN** накопленный fairness score < 80%
- **THEN** система создаёт задачу `tech-debt:bias-audit`
