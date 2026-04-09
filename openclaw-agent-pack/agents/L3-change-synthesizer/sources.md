# L3 Sources

Перед запуском `L3 Change Synthesizer` сначала прочитай этот файл.

## Назначение

Этот файл задаёт, из каких источников `L3` имеет право строить или обновлять change streams.

## Primary Inputs

- `L4` evidence entries из project folders
- `L4` evidence entries из `shared-intelligence`
- `L4` evidence entries из `triage/inbox`, если они уже partially classified

## Supporting Inputs

- карта ownership зон `L2`
- список активных change streams
- список strategic goals

## Change Stream Construction Rules

- change stream строится только на основе уже опубликованного `L4`
- один stream может агрегировать несколько evidence entries
- stream не создаётся без попытки определить `owning_l2`

## Ownership Rules

- каждый `L3` stream обязан иметь один `owning_l2`
- дополнительные зоны указываются как `contributing_l2`
- если ownership не определён, допускается только `needs-l2-assignment`

## Cross-project Rules

- один stream может иметь `primary_project` и несколько `related_projects`
- cross-project stream не означает shared ownership
- shared ownership заменяется на single owner + explicit contributors
