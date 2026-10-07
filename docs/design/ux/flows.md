# UX Flows

## Flow 1: Screening -> Shortlist
1. Рекрутёр открывает дашборд вакансии.
2. Видит список кандидатов со score.
3. Кликает на кандидата -> карточка.
4. Данные маскированы (TokenBadge: masked).
5. Кликает "Показать PII" -> reveal + audit log.
6. Принимает решение -> shortlist / reject.
7. Feedback автоматически уходит в ATS.

## Flow 2: Consent Revocation
1. Кандидат отзывает согласие (email / UI).
2. Consent API -> hard trigger.
3. Метка consent-revoked на всех артефактах.
4. Circuit Breaker: пайплайны остановлены.
5. Purge Pipeline: Git, Vector Index, MCP Logs.
6. Audit Vault: запись "Purge выполнен".
7. Рекрутёр видит уведомление в UI.

## Flow 3: Batch Screening (фоновый)
1. Рекрутёр загружает 10 резюме.
2. Pre-commit hook: PII-детектор.
3. Gitea Actions: Semgrep PII (Block).
4. Tokenizer: PII -> Token.
5. LLM Gateway -> GigaChat 3 Lightning (batch).
6. Scorecard + риски.
7. Re-identification в UI рекрутёра.
8. Self-Check Report.