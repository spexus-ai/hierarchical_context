# Skill: execute_task

Название: execute_task

Задача:
Выполнить изменение (код, конфиг, данные).

Выход:

actions:
- <что сделано>

artifacts:
- <PR, commit, config change>

status:
- success|partial|failed

Правила:
- каждое действие → trace
- не делать скрытых изменений
