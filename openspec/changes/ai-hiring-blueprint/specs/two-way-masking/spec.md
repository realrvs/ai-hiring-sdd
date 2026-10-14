## ADDED Requirements

### Requirement: Детерминированная токенизация

Система SHALL заменять PII на детерминированные токены.

#### Scenario: Токенизация PII

- **WHEN** текст содержит PII
- **THEN** система заменяет PII на токен и сохраняет соответствие в Token Vault

### Requirement: Token Vault

Система SHALL хранить Token Vault on-prem с шифрованием AES-256 и RBAC.

#### Scenario: Re-identification в UI рекрутера

- **WHEN** рекрутёр запрашивает демаскирование
- **THEN** система проверяет RBAC и выполняет re-identification

#### Scenario: Аудит демаскирования

- **WHEN** выполняется демаскирование
- **THEN** система записывает в Audit Vault: кто, когда, какой токен

### Requirement: Read-only режим при недоступности Tokenizer

Система SHALL переходить в read-only режим при недоступности Tokenizer и блокировать новые скрининги.

#### Scenario: Tokenizer недоступен

- **WHEN** Tokenizer недоступен
- **THEN** система включает read-only режим и блокирует новые скрининги
