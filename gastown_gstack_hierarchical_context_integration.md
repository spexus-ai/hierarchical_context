# Gastown, gstack, hierarchical_context

## Purpose

Этот документ фиксирует предложения по тому, как связать между собой:

- `gastown`
- `gstack`
- `hierarchical_context`

Цель не в том, чтобы слить их в одну систему, а в том, чтобы развести роли и
сделать их совместимыми.

---

## Short Answer

Рекомендуемая модель:

- `gastown` = execution and coordination plane
- `gstack` = methodology and specialist plane
- `hierarchical_context` = shared knowledge and strategy plane

То есть:

- `gastown` отвечает за orchestration, dispatch, work tracking, handoffs, attribution
- `gstack` отвечает за то, как думать, проверять, ревьюить, планировать и извлекать repeatable learnings
- `hierarchical_context` отвечает за внешнюю, общую, git-backed систему накопления знаний и связи проектов со стратегией

---

## Why Not Merge Them

Не стоит делать один общий storage layer для всех трёх систем.

### Почему не хранить всё в gstack

`gstack` уже хранит learnings и timeline локально в `~/.gstack/projects/...`.
Это хорошо для персональной и проектной памяти, но плохо как источник общей
организационной истины:

- storage локален машине/пользователю
- нет общей структуры L0-L4
- нет явной модели ownership / portfolio / strategic goals

### Почему не хранить всё в gastown

`gastown` силён как execution substrate:

- rigs
- crew
- polecats
- convoys
- hooks
- beads
- mail
- seance
- Wasteland

Но это operational memory, а не shared strategic knowledge base.

Если запихнуть в него `hierarchical_context`, появятся проблемы:

- смешение operational state и стратегического контекста
- тяжёлая навигация по знаниям
- высокий риск дублирования и drift

### Почему hierarchical_context должен быть отдельным

`hierarchical_context` логично держать как отдельный git-backed HQ knowledge repo:

- append-only evidence на `L4`
- change streams на `L3`
- ownership boundaries на `L2`
- domains/streams на `L1`
- portfolio strategy и goals на `L0`

Это shared artifact для нескольких команд, агентов и проектов.

---

## Recommended System Roles

## 1. Gastown

`gastown` должен остаться системой исполнения и координации.

Что ему подходит:

- multi-agent orchestration
- dispatch
- convoy tracking
- persistent agent identity
- hooks and handoffs
- issue / bead lifecycle
- escalation
- seance
- Wasteland federation

Что ему не стоит делать:

- быть primary store для strategic context
- быть единственным местом хранения cross-project knowledge
- хранить canonical portfolio narrative

## 2. gstack

`gstack` должен остаться системой skill-based methodology.

Что ему подходит:

- planning workflows
- review workflows
- QA workflows
- retro workflows
- reusable learnings
- cross-project pattern recall

Что ему не стоит делать:

- быть shared organizational memory of record
- быть execution orchestrator for a whole town
- хранить canonical ownership and strategy model

## 3. hierarchical_context

`hierarchical_context` должен стать внешней системой контекста и смысла.

Что ему подходит:

- shared knowledge repo
- evidence accumulation
- cross-project linking
- ownership modeling
- strategy mapping
- portfolio visibility

Что ему не стоит делать:

- быть task runner
- быть low-level dispatch engine
- заменять issue tracker / convoy tracker / hooks

---

## Proposed Integration Model

## Core Principle

Связывать системы не через общий storage, а через export/import bridge.

То есть:

- `gastown` экспортирует operational evidence в `hierarchical_context`
- `gstack` экспортирует specialist evidence and learnings в `hierarchical_context`
- `hierarchical_context` отдаёт обратно нормализованный контекст в `gastown` и `gstack`

---

## Data Flow

## 1. gastown -> hierarchical_context

`gastown` становится главным producer для `L4` и частью producer для `L3`.

Какие артефакты экспортировать:

- bead creation / update / close
- convoy create / status / land
- sling / dispatch events
- escalation events
- hook artifacts
- mail threads
- seance summaries
- witness / deacon / dog findings
- Wasteland claims / completions / stamps

Как это ложится в иерархию:

- `L4` = raw evidence and event records
- `L3` = change streams, issue streams, incident streams, execution streams
- `L2` = rig, crew specialization, owned repo/service/capability

Идея:

- `gastown` знает, что произошло
- `hierarchical_context` знает, что это значит в общей картине

## 2. gstack -> hierarchical_context

`gstack` должен экспортировать не все внутренности, а структурированные результаты skills.

Что экспортировать:

- `/office-hours` outputs
- `/plan-*` outputs
- `/autoplan` results
- `/review` findings
- `/qa` findings
- `/cso` findings
- `/benchmark` outputs
- `/retro` outputs
- `/learn` entries

Как это использовать:

- planning outputs = `L4` evidence + input для `L3`
- review outputs = `L4` evidence
- retros = `L4` evidence + агрегация для `L1/L0`
- learnings = `L4` pattern/pitfall evidence, часто reusable между проектами

Важно:

- `gstack` не должен быть canonical source
- он должен быть specialist evidence producer

## 3. hierarchical_context -> gastown

Это обратная связь в routing and dispatch.

`gastown` уже двигается в сторону capability-based dispatch:

- capability claims
- routing examples
- anti-examples
- trust via evidence
- bounce-as-learning

Это очень хорошо маппится на `L2`.

Предлагаемый use:

- `L2` хранит canonical ownership/capability profile
- Mayor читает `L2` перед dispatch
- bounce events и completions из `gastown` обновляют `L4`
- `L4 -> L3 -> L2` пересборка уточняет capability profile

Итого:

- `gastown` не изобретает отдельно второй слой knowledge profiles
- `hierarchical_context.L2` становится внешним capability/ownership memory

## 4. hierarchical_context -> gstack

`gstack` можно сделать context-aware specialist layer.

Примеры:

- `/review` читает relevant `L2/L3/L4` перед ревью
- `/office-hours` и `/plan-ceo-review` читают `L0/L1`
- `/retro global` публикует выводы в `L1/L0`
- `/learn` может синхронизировать project-local insights в shared `L4`

Итого:

- `gstack` остаётся методологией
- но начинает работать на уже накопленном shared context

---

## Canonical Architecture

Лучший первый вариант:

1. отдельный `hierarchical_context` repo как HQ knowledge repo
2. `gastown-exporter`
3. `gstack-exporter`
4. readers обратно в `gastown` и `gstack`

### gastown-exporter

Читает:

- beads
- convoys
- hooks
- events
- mail
- seance
- Wasteland

Пишет:

- canonical `L4` entries
- links в `L3` streams

### gstack-exporter

Читает:

- `~/.gstack/projects/*/learnings.jsonl`
- `timeline.jsonl`
- review outputs
- QA outputs
- plan outputs
- retro outputs

Пишет:

- `L4` evidence entries
- иногда signals для `L3`
- cross-project pattern evidence в `shared-intelligence`

### Read path

- `gastown` читает `L2/L3` для routing and ownership context
- `gstack` читает `L0-L4` для better planning, review, QA, retro

---

## Entity Mapping

Ниже предлагаемый маппинг сущностей.

| Source system | Entity | hierarchical_context target |
|---|---|---|
| gastown | rig | `L2` ownership zone or `L1` domain anchor |
| gastown | crew specialization | `L2` capability/ownership node |
| gastown | bead / issue | `L3` change stream or issue stream |
| gastown | convoy | `L3` execution/change stream |
| gastown | hook event | `L4` evidence |
| gastown | mail thread | `L4` evidence |
| gastown | seance output | `L4` evidence |
| gastown | escalation | `L3` incident/escalation stream + `L4` evidence |
| gastown | Wasteland stamp | `L4` evidence, possible `L2` trust signal |
| gstack | learning | `L4` reusable pattern/pitfall evidence |
| gstack | review finding | `L4` review evidence |
| gstack | QA finding | `L4` QA evidence |
| gstack | office-hours / plan output | `L4` planning evidence, possible `L3` initiative seed |
| gstack | retro output | `L4` retrospective evidence, input to `L1/L0` |

---

## How L2 Should Work Across the Three Systems

`L2` должен стать центральной точкой согласования ownership и capability.

Это важно, потому что:

- `gastown` хочет capability-based dispatch
- `gstack` хочет specialist routing
- `hierarchical_context` хочет ownership boundaries

### Recommended L2 meaning

`L2` = canonical zone of responsibility.

Это может быть:

- git repository
- service
- platform component
- analytics pipeline
- market intelligence function
- security function
- shared capability team

### Recommended L2 fields

- `zone_id`
- `zone_type`
- `owned_assets`
- `handles`
- `does_not_handle`
- `example_tasks`
- `anti_examples`
- `dependencies`
- `strategic_contributions`
- `knowledge_imports`
- `knowledge_exports`

Это хорошо скрещивает:

- ownership model из `hierarchical_context`
- capability profiles из `gastown`
- specialist routing from `gstack`

---

## How L3 Should Work

`L3` не должен быть просто “списком задач”.

Лучше считать его stream layer:

- issue stream
- initiative stream
- execution stream
- incident stream
- escalation stream
- migration stream

### Источники L3

- из `gastown`: convoys, escalations, bead clusters
- из `gstack`: approved plans, repeated review/QA findings, strategic change proposals
- из `hierarchical_context`: aggregation over `L4`

### Constraint

Каждый `L3` stream обязан принадлежать конкретному `L2`.

Если это cross-project stream:

- один `owning_l2`
- остальные как `contributing_l2`

---

## How L4 Should Work

`L4` должен быть canonical shared evidence layer.

### Storage principle

- один project folder = одна project knowledge area
- одна evidence entry = один файл
- cross-links вместо дублирования
- `shared-intelligence` для непроектных потоков
- `triage` для неразмеченного

### Who writes to L4

- gastown exporter
- gstack exporter
- manual team contributions
- future external collectors

### What belongs in shared-intelligence

Полезные общие потоки:

- market intelligence
- customer intelligence
- partner/vendor intelligence
- regulatory intelligence
- security intelligence
- operations intelligence
- hiring/talent intelligence
- GTM/sales intelligence

Не все из них нужны сразу, но сама модель должна их допускать.

---

## What Not To Do

## 1. Do not unify storage too early

Не нужно сразу тащить:

- gstack learnings
- gastown beads
- hooks state
- L0-L4 context

в одну физическую базу.

Сначала нужен clean contract.

## 2. Do not make gstack the source of truth

`gstack` хорош как specialist methodology layer, но не как shared truth layer.

## 3. Do not make beads the strategic memory

Beads отлично подходят для tracked work, но хуже подходят для portfolio knowledge.

## 4. Do not force a universal taxonomy

`gastown` design notes правильно подсказывают:

- claims
- examples
- anti-examples
- evidence

полезнее, чем жёсткая централизованная taxonomy.

## 5. Do not start with real-time sync

Сначала достаточно:

- daily batch export
- event-triggered export for important events

Реалтайм можно добавить позже.

---

## Recommended Rollout Order

## Phase 1

Сделать `hierarchical_context` внешним HQ repo.

Результат:

- есть место, куда может складываться shared context

## Phase 2

Подключить `gastown` как главный producer для `L4/L3`.

Результат:

- execution reality начинает отражаться в shared context

## Phase 3

Подключить `gstack` как specialist evidence producer.

Результат:

- review/QA/plan/retro/learnings начинают накапливаться в общей памяти

## Phase 4

Сделать обратное чтение:

- Mayor читает `L2/L3`
- gstack skills читают `L0-L4`

Результат:

- execution и methodology начинают работать на общей knowledge base

## Phase 5

Добавить portfolio-level automation:

- strategic goals on `L0`
- project contribution mapping
- capability trust signals
- cross-project knowledge reuse suggestions

---

## Final Recommendation

Если коротко:

- `gastown` отвечает за: кто делает и что происходит
- `gstack` отвечает за: как качественно думать и выполнять
- `hierarchical_context` отвечает за: что это всё значит для портфеля и как знания накапливаются

Это не конкурирующие системы.
Это три разных слоя одной будущей архитектуры.

Наиболее здоровый путь интеграции:

- не слияние
- не переписывание
- не новая суперсистема

а:

- shared knowledge repo
- exporters
- readers
- постепенное замыкание обратной связи
