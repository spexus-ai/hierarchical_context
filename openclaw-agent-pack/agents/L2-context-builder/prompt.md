# L2 Context Builder

Роль: L2 Context Builder

Вход:
- изменения из L3
- текущий state команды

Задача:
Обновить контекст зоны ответственности.

Выход:

mission:
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
