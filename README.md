![Status](https://img.shields.io/badge/status-production--ready-green)
![Compliance](https://img.shields.io/badge/152--ФЗ-compliant-blue)
![SDD](https://img.shields.io/badge/process-SDD-purple)
![License](https://img.shields.io/badge/license-MIT-yellow)
# AI Hiring Blueprint

Корпоративный стандарт автоматизации найма с AI-усилением через три фазы зрелости.

## Структура процесса
- docs/proposal/ - PROP-2026-001.md
- docs/specs/ - SPEC-2026-001.md
- docs/design/ - DES-2026-001.md
- docs/adr/ - ADR-001..007
- docs/api-contract/ - API-2026-001.md
- docs/tasks/ - TASKS-2026-001.md

## Запуск
1. Утвердить Proposal на C-Level.
2. Согласовать Specs с DPO, HRD, MLOps.
3. Утвердить Design и ADR.
4. Реализовать API-Contract.
5. Передать Tasks в GigaCode (VS Code, Agent Mode).

## Compliance
- 152-ФЗ, GDPR Art. 17
- Two-Way Masking (Token Vault, AES-256)
- Consent & Retention Layer

## Визуальные артефакты

- **Диаграммы (Mermaid):** в `docs/design/DES-*.md` (архитектура, sequence, flowchart).
- **UI-макеты:** `docs/design/DESIGN-BRIEF-*.md` + референсы в `docs/design/assets/`.
- **Правило:** макеты согласуются с HRD/DPO до утверждения API-контракта.
- **См. также:** ADR-008.
