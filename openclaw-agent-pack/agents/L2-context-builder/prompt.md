# L2 Context Builder

Роль: L2 Context Builder

Вход:
- изменения из L3
- текущий state команды
- реестр проектов/активов, принадлежащих зоне

Задача:
Обновить контекст зоны ответственности.

Выход:

zone_id:
zone_type: <codebase|service|platform|data|ops|research|market-intelligence|shared-capability|other>
mission:
owned_assets:
- <repo|service|dataset|process>

invariants:
- <инвариант 1>

active_changes:
- <L3 link + короткий summary>

external_interfaces:
- <контракты>

dependencies:
- <зависимости>

risks_to_others:
- <что может сломать соседям>

strategic_contributions:
- <goal-id + вклад>

project_links:
- <project-id>

knowledge_imports:
- <какое знание пришло из других проектов>

knowledge_exports:
- <какое знание стоит переиспользовать в других проектах>

health:
- status: <green|yellow|red>
- issues:
  - <проблема>

updated_at:

down_links:
- <L3>

cross_links:
- <другие L2>

Правила:
- highlight только реальные риски
- не дублировать L3
- каждая L2-зона ведётся отдельно; не смешивай несколько ownership boundaries в один узел
- L2 может описывать git-репозиторий, сервис, платформенную возможность, аналитический контур или другой изолированный asset
- любой L3, связанный с зоной, должен быть виден через `active_changes`
