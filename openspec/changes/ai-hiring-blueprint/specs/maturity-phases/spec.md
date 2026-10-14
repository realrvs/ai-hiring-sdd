## ADDED Requirements

### Requirement: Поддержка трёх фаз зрелости

Система SHALL поддерживать режимы Assist, Augment и Autonomous.

#### Scenario: Активация фазы Assist

- **WHEN** система находится в фазе Assist
- **THEN** AI выполняет подготовительные действия, а финальное решение принимает человек

#### Scenario: Активация фазы Augment

- **WHEN** система переведена в фазу Augment
- **THEN** AI ведёт процесс, а человек валидирует результат на контрольных точках

#### Scenario: Активация фазы Autonomous

- **WHEN** система переведена в фазу Autonomous
- **THEN** AI закрывает вакансию полностью, человек участвует только в финальном оффере

### Requirement: Gate-переход между фазами

Система SHALL переводить между фазами только через Gate с метриками: минимум 2 квартала на фазе, 100% Purge SLA, 0 критических инцидентов.

#### Scenario: Успешный переход фазы

- **WHEN** все критерии Gate выполнены
- **THEN** система разрешает переход на следующую фазу

#### Scenario: Блокировка перехода Фаза 1 → Фаза 3

- **WHEN** запрошен переход из Assist сразу в Autonomous
- **THEN** Policy Enforcement блокирует переход и фиксирует инцидент

### Requirement: Fast-Track и Hotfix

Система SHALL поддерживать Fast-Track по метке `fast-track` и Hotfix по решению HRD/CEO.

#### Scenario: Активация Fast-Track

- **WHEN** PR помечен `fast-track` и критерии выполнены
- **THEN** Gitea Actions автоматически пропускает PR

#### Scenario: Отклонение Fast-Track

- **WHEN** критерии Fast-Track не выполнены
- **THEN** метка снимается, заявка блокируется

#### Scenario: Hotfix с Consent-проверкой

- **WHEN** Hotfix активирован HRD/CEO
- **THEN** система выполняет обязательную Consent-проверку и создаёт Post-Mortem с JD/Scorecard
