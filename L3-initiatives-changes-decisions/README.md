# L3 — Initiatives / Changes / Decisions

## Что это

Операционный уровень изменений.

Единица этого уровня — конкретный объект управления:
- инициатива;
- change;
- decision;
- incident;
- migration;
- experiment;
- refactor.

Именно здесь фиксируется:
- что меняется;
- зачем;
- кого это затрагивает;
- какие есть риски;
- на что смотреть дальше.

## Задачи уровня

- делать изменения наблюдаемыми;
- связывать intent и implementation;
- давать summary изменений для соседей;
- обеспечивать drill-down в evidence;
- уменьшать surprise-эффект при релизах и интеграции.
- агрегировать evidence в change streams по проектам и ownership zones, а не складывать всё в один поток.

## Какие решения принимаются

- запускать или откладывать изменение;
- кого нужно уведомить;
- какие риски приемлемы;
- какие проверки обязательны;
- где нужен rollback / mitigation plan.

## Обязательные поля карточки изменения

- `title`
- `change_stream_id`
- `portfolio_id`
- `primary_project`
- `owning_l2`
- `why`
- `scope`
- `affected_areas`
- `expected_value`
- `risks`
- `status`
- `owner`
- `updated_at`
- `links_to_L4`

## Дополнительные правила

- каждый change stream обязан принадлежать конкретной зоне `L2`;
- если ownership не определён, узел не считается валидным L3 и должен быть отправлен в triage;
- один change stream может иметь несколько `related_projects`, но primary owner на уровне `L2` всегда один.
