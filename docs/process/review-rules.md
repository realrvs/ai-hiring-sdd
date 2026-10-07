# Правила ревью по этапам

## Общие правила

1. **Один Accountable на этап.** Только он нажимает Merge.
2. **Consulted обязан дать ревью** в течение 24 часов.
3. **Informed не блокирует** merge.
4. **Нельзя мёржить PR с незакрытыми needs-*-review.**
5. **Back-propagation обязателен**, если изменение затрагивает предыдущие этапы.

## По этапам

### Proposal
- **Accountable:** Product Owner
- **Consulted:** Аналитик, Дизайнер, Архитектор, DPO
- **Informed:** Тимлид, Разработчик, Process Owner
- **Что проверяют:** бизнес-целесообразность, исполнимость, compliance.

### Specs
- **Accountable:** Аналитик
- **Consulted:** Дизайнер, Архитектор, DPO
- **Informed:** Product Owner, Тимлид, Process Owner
- **Что проверяют:** покрытие FR, edge cases, отсутствие технических деталей.

### ADR (Draft)
- **Accountable:** Архитектор
- **Consulted:** Аналитик, Дизайнер, DPO
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** ограничения по latency, PII, бюджету.

### Design (системный)
- **Accountable:** Архитектор
- **Consulted:** Аналитик, Дизайнер, DPO
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** целостность, покрытие FR.

### Design (UX)
- **Accountable:** Дизайнер
- **Consulted:** Аналитик, Архитектор, DPO
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** user flows, состояния, a11y, PII-индикация.

### ADR (Final)
- **Accountable:** Архитектор
- **Consulted:** Аналитик, Дизайнер, DPO
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** финальные решения, отсутствие противоречий с Design.

### API-contract
- **Accountable:** Архитектор
- **Consulted:** Аналитик, Дизайнер, DPO, Тимлид
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** endpoints, RBAC, ошибки, семантика полей.

### Tasks
- **Accountable:** Тимлид
- **Consulted:** Аналитик, Дизайнер, Архитектор
- **Informed:** Product Owner, Process Owner
- **Что проверяют:** атомарность, критерии приёмки, зависимости.

### Apply
- **Accountable:** Разработчик / Агент
- **Consulted:** Аналитик (functional), Дизайнер (visual), DPO (compliance)
- **Informed:** Product Owner, Архитектор, Process Owner
- **Что проверяют:** соответствие Specs, API, UX; Self-Check Report.