# L4 Evidence Entry Template

Используется для одной canonical записи evidence.
Одна запись = один файл.

Поддерживаемые режимы:
- `portfolio-project` — evidence конкретного проекта
- `shared-intelligence` — общий поток знаний без одного primary проекта
- `triage` — временное размещение, если проект / owner пока не определён

## Metadata
- entry_id:
- title:
- type: <pr|commit|adr|incident|metric|ticket|discussion|market-signal|customer-signal|regulatory-signal|security-signal|operations-signal|other>
- level: L4
- storage_scope: <portfolio-project|shared-intelligence|triage>
- portfolio_id:
- project_id:
- shared_stream_id:
- related_projects:
  - <project-id>
- source_system:
- source_type:
- source_ref:
- collected_by:
- owner:
- owning_l2_candidates:
  - <zone-id>
- strategic_goal_candidates:
  - <goal-id>
- confidence: <low|medium|high>
- created_at:
- updated_at:

## Fact Summary
Кратко, что появилось в источнике без интерпретации уровня L3+.

## Facts
- <проверяемый факт 1>
- <проверяемый факт 2>

## Signals
### Metric Changes
- <метрика + изменение>

### Anomalies
- <аномалия>

### Operational Signals
- <наблюдение>

## Impact Candidates
- <что потенциально затронуто>

## Cross-project Reuse Candidates
- <где это знание может пригодиться ещё>

## Raw Artifacts
- <url/path to PR, dashboard, ticket, report, log, transcript>

## Publishing Notes
- canonical_path:
- journal_ref:
- dedup_key:
- supersedes:
  - <entry-id>

## Routing Notes
- если `storage_scope = portfolio-project`, `project_id` обязателен
- если `storage_scope = shared-intelligence`, `shared_stream_id` обязателен
- если `storage_scope = triage`, нужно явно указать, что не удалось определить: `project_id`, `owning_l2` или оба
