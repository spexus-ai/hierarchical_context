# OpenClaw Agent Pack

Архив с агентскими промптами для контекстного дерева L0–L4, ежедневного координатора и отдельного OpenClaw execution agent со скиллами.

## Состав

- `agents/common/system-preamble.md` — общие правила для всех агентов
- `agents/L4-evidence-extractor/prompt.md`
- `agents/L3-change-synthesizer/prompt.md`
- `agents/L2-context-builder/prompt.md`
- `agents/L1-domain-aggregator/prompt.md`
- `agents/L0-global-synthesizer/prompt.md`
- `agents/daily-orchestrator/prompt.md`
- `agents/context-router/prompt.md`
- `agents/openclaw-execution-agent/prompt.md`
- `agents/openclaw-execution-agent/skills/*.md`

## Рекомендуемый порядок работы

1. L4 извлекает факты из первички
2. L3 собирает карточки изменений
3. L2 обновляет контекст команды / подсистемы
4. L1 агрегирует домен
5. L0 даёт глобальную картину
6. Daily Orchestrator проверяет свежесть и согласованность
7. OpenClaw исполняет задачу на основании L3 и публикует evidence в L4

## Принцип

- summary идёт сверху вниз
- доказательства идут снизу вверх
- исполнение разрешено только при наличии L3-узла и проверке инвариантов
