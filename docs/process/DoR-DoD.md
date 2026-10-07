# Definition of Ready / Definition of Done

## Definition of Ready (DoR) - критерий перехода на следующий этап

| Переход | Критерий |
|---|---|
| Proposal -> Specs | Утверждён C-Level, согласован с DPO |
| Specs -> ADR (Draft) | Все FR покрыты, edge cases описаны, UX-требования зафиксированы |
| ADR (Draft) -> Design | Ограничения по latency, PII, бюджету зафиксированы |
| Design -> ADR (Final) | Системная и UX-части согласованы, нет противоречий |
| ADR (Final) -> API-contract | Все архитектурные решения приняты |
| API-contract -> Tasks | Все endpoints описаны, RBAC проверен |
| Tasks -> Apply | Задачи атомарны, критерии приёмки ясны |

## Definition of Done (DoD) - критерий завершения этапа

- [ ] Все обязательные ревьюеры approved
- [ ] Все needs-*-review сняты
- [ ] Артефакт закоммичен в main
- [ ] Self-Check Report сгенерирован (для Apply)
- [ ] Impact on Blueprint Metrics зафиксирован
- [ ] Нет открытых back-propagation без ссылок на PR

## SLA ревью

| Роль | SLA |
|---|---|
| Accountable | 4 часа |
| Consulted | 24 часа |
| Informed | не блокирует |

Если SLA нарушен - эскалация к Process Owner.