# Процесс SDD - AI Hiring Blueprint

## Артефакты процесса
- [RACI Matrix](RACI.md) - кто за что отвечает
- [DoR / DoD](DoR-DoD.md) - критерии перехода и завершения
- [Back-propagation](back-propagation.md) - правила откатов
- [Метрики](metrics.md) - метрики процесса
- [Правила ревью](review-rules.md) - по этапам

## Пайплайн

~~~text
Proposal
   |
   v
Specs
   |
   v
ADR (Draft, constraints)
   |
   v
Design (системный)  <--->  Design (UX)
   |
   v
ADR (Final, decisions)
   |
   v
API-contract
   |
   v
Tasks
   |
   v
Apply
~~~

## Ключевые правила

1. **Один Accountable на этап.** Если их два - это баг.
2. **Back-propagation обязателен** при изменении предыдущих этапов.
3. **DPO / Compliance** - обязательный Consulted для PII.
4. **Process Owner** следит за актуальностью процесса.
5. **Метрики** собираются автоматически через GitHub Actions.

## Роли

| Роль | Ответственность |
|---|---|
| Product Owner | Бизнес-целесообразность |
| Аналитик | Specs (поведение) |
| Дизайнер | Design (UX-дерево) |
| Архитектор | ADR, Design (системный), API-contract |
| DPO | Compliance (PII, 152-ФЗ) |
| Тимлид | Tasks |
| Разработчик / Агент | Apply |
| Process Owner | Актуальность процесса, метрики, ретро |