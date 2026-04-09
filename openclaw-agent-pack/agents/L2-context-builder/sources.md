# L2 Sources

Перед запуском `L2 Context Builder` сначала прочитай этот файл.

## Назначение

Этот файл задаёт источники, на которых разрешено пересобирать ownership context.

## Primary Inputs

- change streams из `L3`
- текущий state зоны ответственности
- registry проектов и активов, принадлежащих зоне

## Supporting Inputs

- historical `L4` evidence, если нужен drill-down
- cross-links на соседние `L2`
- strategic goals, в которые зона делает вклад

## Ownership Boundary Rules

- одна `L2` зона = один ownership boundary
- boundary может описывать repo, service, platform capability, data pipeline, intelligence function или shared capability
- не смешивай несколько ownership boundaries в одном `L2` узле

## Update Rules

- `L2` должен пересобираться только из релевантных `L3`
- `L2` не дублирует содержимое `L3`, а описывает устойчивый operational context
- если изменение не может быть привязано к зоне, оно не должно silently попадать в `L2`
