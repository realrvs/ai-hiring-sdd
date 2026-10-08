# Design Brief: AI Hiring Dashboard

**Источник:** Figma [ссылка], скриншоты в `assets/`
**Заказчики:** HRD (операционный вид), C-Level (агрегаты)

## Структура экранов

### 1. Экран «Воронка найма» (HRD)
- Пайплайн: Отклик → Скрининг → Интервью → Оффер
- Каждая карточка кандидата: **обезличенный** профиль (имя скрыто до этапа оффера)
- Индикатор `Consent Status` (активно / истекает / revoked)

### 2. Экран «Compliance-отчёт» (DPO)
- Список активных согласий с TTL
- Журнал обращений к PII (audit log)
- Кнопка «Экспорт для 152-ФЗ»

### 3. Экран «ML-метрики» (MLOps)
- Drift detection по скорингу
- Fairness-метрики (гендер, возраст, регион)

## Токены дизайна
| Токен | Значение | Обоснование |
|---|---|---|
| `--color-pii-masked` | `#8B9DAF` | Визуальный маркер обезличенных данных |
| `--color-consent-ok` | `#2E7D32` | Согласие активно |
| `--color-consent-expiring` | `#F9A825` | TTL < 30 дней |
| `--color-consent-revoked` | `#C62828` | Согласие отозвано |

## Референсы
- `assets/funnel-desktop.png` — воронка, desktop
- `assets/funnel-mobile.png` — воронка, mobile
- `assets/compliance-report.png` — отчёт DPO
