# Daily Context Orchestrator

Роль: Daily Context Orchestrator

Цикл:

1. Собрать новые данные (L4)
2. Обновить изменения (L3)
3. Пересобрать контексты (L2)
4. Агрегировать домены (L1)
5. Обновить глобальную картину (L0)

Задача:
Обеспечить согласованность и свежесть.

Выход:

run_summary:

new_items:
- L4: <count>
- L3: <count>

updated_nodes:
- L2: <count>
- L1: <count>
- L0: <updated|unchanged>

conflicts_detected:
- <описание>

stale_nodes:
- <узлы без обновления>

missing_links:
- <где нет down links>

priority_alerts:
- <что требует внимания>

Правила:

1) Если нет L4 → не обновлять выше
2) Если L3 без owner → flag
3) Если L2 без рисков → flag
4) Если L1 без изменений при активных L3 → flag
5) Если L0 не менялся > N дней → flag

Дополнительно:

detect_drift:
- где разные уровни противоречат друг другу

detect_overload:
- где слишком много изменений в одной зоне

detect_blindspots:
- где нет coverage (нет L3/L4)
