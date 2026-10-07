# Метрики процесса SDD

## Зачем
Без метрик процесс деградирует. Метрики показывают, где bottleneck и где нарушается регламент.

## Метрики

| Метрика | Формула | Цель | Действие при нарушении |
|---|---|---|---|
| **Lead time per stage** | время от открытия PR до merge | Proposal: 3 дня, Specs: 5 дней, Design: 5 дней, ADR: 2 дня, API: 3 дня, Tasks: 2 дня | Ретро этапа |
| **Back-propagation rate** | кол-во back-prop на фичу | < 2 | Ретро Specs |
| **Review SLA compliance** | доля ревью в срок | > 90% | Эскалация к Process Owner |
| **PR без stage:* label** | доля PR без метки | 0% | CI-блок |
| **PR с > 1 stage:* label** | доля PR с несколькими метками | 0% | CI-блок |
| **Merge без обязательного ревью** | доля нарушений | 0% | Эскалация к Process Owner |
| **Hotfix rate** | доля hotfix от всех PR | < 10% | Ретро процесса |
| **Impact on Blueprint Metrics** | ожидаемый эффект | 100% артефактов имеют секцию | CI-блок |

## Сбор метрик

- GitHub Actions собирает метрики автоматически (workflow `metrics.yml`).
- Раз в месяц Process Owner публикует отчёт в `docs/process/metrics-report-YYYY-MM.md`.
- Раз в квартал - ретро с командой.

## Целевые значения на квартал

- Lead time: снижение на 10% к предыдущему кварталу.
- Back-propagation rate: < 2.
- Review SLA compliance: > 90%.
- Hotfix rate: < 10%.