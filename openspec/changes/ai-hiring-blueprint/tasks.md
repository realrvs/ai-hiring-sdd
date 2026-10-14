## 1. Фаза 0: Инфраструктура

- [ ] 1.1 T-001: Развернуть Gitea On-premise (infra/gitea/docker-compose.yml)
- [ ] 1.2 T-002: Настроить Gitea Actions (.gitea/workflows/ci.yml)
- [ ] 1.3 T-003: Развернуть HR LLM Gateway (infra/gateway/config.yaml)
- [ ] 1.4 T-004: Развернуть Anonymization Tokenizer + Token Vault (infra/tokenizer/docker-compose.yml)

## 2. Фаза 1: Assist (Human-in-the-Loop)

- [ ] 2.1 T-101: Реализовать Intake Agent (agents/intake/agent.py)
- [ ] 2.2 T-102: Реализовать Sourcing Agent (agents/sourcing/agent.py)
- [ ] 2.3 T-103: Реализовать Screening Agent batch (agents/screening/agent.py)
- [ ] 2.4 T-104: Реализовать Interview Kit Generator (agents/interview/agent.py)
- [ ] 2.5 T-105: Реализовать Offer Calculator (agents/offer/agent.py)

## 3. Фаза 1: Compliance

- [ ] 3.1 T-110: Реализовать Consent API (agents/consent/api.py)
- [ ] 3.2 T-111: Реализовать Purge Pipeline (scripts/purge_pipeline.py)
- [ ] 3.3 T-112: Настроить Semgrep PII Block mode (.gitea/workflows/pii-scan.yml)
- [ ] 3.4 T-113: Реализовать Bias Detection diff-based (agents/bias/detector.py)

## 4. Фаза 2: Augment (Human-on-the-Loop)

- [ ] 4.1 T-201: Внедрить контрольные точки (agents/platform/checkpoints.py)
- [ ] 4.2 T-202: Настроить Fallback Chain (infra/gateway/fallback.yaml)
- [ ] 4.3 T-203: Внедрить Cost per Hire tracking (scripts/cost_per_hire.py)

## 5. Фаза 3: Autonomous (Human-out-of-the-Loop)

- [ ] 5.1 T-301: Внедрить end-to-end агента (agents/platform/autonomous.py)
- [ ] 5.2 T-302: Внедрить аудит автономных решений (agents/platform/audit.py)
