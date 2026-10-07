# Back-propagation Rules

## Проблема
Линейный транзит Proposal -> Specs -> Design -> ADR -> API -> Tasks -> Apply не работает в реальности.
На поздних этапах всплывают ограничения, требующие возврата.

## Правило
Нельзя вносить правки в API/Tasks, минуя владельцев предыдущих этапов.

## Матрица откатов

| Изменение в | Откатывает | Требует повторного approval |
|---|---|---|
| ADR (Final) | Design | Архитектор, Дизайнер |
| API-contract | Specs, Design | Аналитик, Архитектор |
| Tasks | API-contract, Design | Архитектор |
| Apply (edge case) | Specs, Design, API-contract | Аналитик, Архитектор |
| Hotfix | Specs, Design, API-contract | Архитектор (постфактум) |

## Процедура

1. Автор изменения создаёт PR в целевом этапе.
2. В PR указывает секцию **Back-propagation** с ссылками на затронутые артефакты.
3. Создаёт issue-трейсы в затронутых этапах (метка `back-propagation`).
4. Владельцы затронутых этапов делают ревью в течение 24 часов.
5. Только после approval всех владельцев - merge.

## Метрика
- **Количество back-propagation на фичу.** Если > 2 - Specs плохие, требуется ретро.
- **Время back-propagation.** Если > 48 часов - bottleneck в ревью.

## Fast-Track (Hotfix)

Для production-инцидентов:
- Метка `hotfix` на PR.
- Обязательный только Архитектор (Accountable).
- Постфактум - обновление Specs/Design в течение 48 часов.
- Запись в Post-Mortem.