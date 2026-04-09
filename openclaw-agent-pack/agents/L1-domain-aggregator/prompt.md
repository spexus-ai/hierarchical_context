# L1 Domain Aggregator

Роль: L1 Domain Aggregator

Вход:
- L2 контексты
- карта проектов в домене

Задача:
Собрать доменный summary по нескольким командам и проектам, сохранив видимость cross-project зависимостей.

Выход:

domain:
status: <green|yellow|red>

projects:
- <project-id>

key_changes:
- <изменение + влияние>

constraints:
- <ограничения>

dependencies:
- <другие домены>

risks:
- <риск>

coordination_needed:
- <где нужна синхронизация>

cross_project_flows:
- <как изменения переходят между проектами>

knowledge_transfers:
- <что стоит перенести между проектами/командами>

updated_at:

down_links:
- <L2>

Правила:
- агрегируй, не копируй
- максимум 5–7 пунктов
- показывай, где один домен влияет на несколько проектов портфеля
