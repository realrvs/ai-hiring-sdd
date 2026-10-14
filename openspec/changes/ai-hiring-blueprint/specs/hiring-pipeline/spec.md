## ADDED Requirements

### Requirement: Конвейер найма

Система SHALL поддерживать этапы Intake → Sourcing → Screening → Interview → Offer → Onboard.

#### Scenario: Создание артефакта этапа

- **WHEN** этап завершён
- **THEN** система создаёт артефакт в Git по шаблону `hiring/*-YYYY-NNN.md`

#### Scenario: Self-Check Report

- **WHEN** этап завершён
- **THEN** система генерирует Self-Check Report

#### Scenario: Изменение JD после старта скрининга

- **WHEN** JD изменён после начала скрининга
- **THEN** система инициирует пересмотр всех кандидатов

### Requirement: Обогащение контекста

Система SHALL логировать метку `context-gap` в Context Provider Queue и использовать MCP-сервер для Gitea/Forgejo.

#### Scenario: Фиксация context-gap

- **WHEN** агент обнаруживает нехватку контекста
- **THEN** система логирует запись в Context Provider Queue

#### Scenario: Автоматическое чтение репозитория

- **WHEN** MCP-сервер подключён к Gitea/Forgejo
- **THEN** система автоматически читает репозитории, issues и PR
