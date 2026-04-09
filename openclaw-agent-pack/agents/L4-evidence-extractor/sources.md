# L4 Sources

Перед запуском `L4 Evidence Extractor` сначала прочитай этот файл.

## Назначение

Этот файл задаёт canonical источники сырья для `L4`.
Если источник не описан здесь, агент не должен silently придумывать схему его обработки.

## Source Categories

### Engineering
- pull requests
- commits
- ADR
- CI/CD runs
- incidents
- logs
- dashboards
- traces
- test reports

### Product / Delivery
- tickets
- roadmaps
- release notes
- experiment results
- delivery reports

### Communications
- slack каналы
- telegram сообщения
- email threads
- записи звонков
- meeting notes

### Shared Intelligence
- market intelligence
- customer intelligence
- partner / vendor intelligence
- regulatory intelligence
- security intelligence
- operations intelligence

## Required Source Metadata

Для каждого evidence entry агент должен постараться определить:

- `source_system`
- `source_type`
- `source_ref`
- `collected_by`
- `updated_at`
- `portfolio_id`
- `project_id` или `shared_stream_id`
- `owning_l2_candidates`

## Routing Rules

- если источник относится к конкретному проекту, публикуй в `portfolio/<portfolio-id>/projects/<project-id>/...`
- если источник общий и не имеет одного primary проекта, публикуй в `shared-intelligence/<stream-id>/...`
- если принадлежность не удаётся определить уверенно, публикуй в `triage/inbox/...`

## Dedup Rules

- один canonical факт = один canonical evidence file
- связанные проекты оформляются через `related_projects`
- не дублируй один и тот же артефакт в нескольких project folders
