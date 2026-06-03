ENG
# UX Audit

Hybrid UX audit skill for websites. It combines crawl output, browser interaction, and visual evidence to produce a business-oriented report with prioritized findings and actionable recommendations.

This version is designed to reduce false negatives from text-only crawling and to make the audit more defensible with screenshots, confidence levels, and explicit evidence tracking.

## What it does

The skill audits a site across six blocks:

1. Nielsen heuristics
2. Conversion
3. Content
4. Technical and visual quality
5. Information architecture
6. Accessibility quick pass

It supports:

- quick audits for small sites
- evidence-heavy audits for commercial landing pages and service sites
- large-site audits based on template sampling
- competitor comparison
- fix specifications for implementation

## Why this version is stronger

Compared with a text-only crawl workflow, this version adds:

- engine selection by job type
- explicit site mapping before evaluation
- browser checks for forms, menus, and mobile states
- screenshots as evidence
- page-template sampling for large sites
- confidence levels on every finding
- a separate evidence artifact to distinguish facts from inferences
- an accessibility quick pass by default

## Recommended tool roles

| Tool | Best use |
|---|---|
| `Playwright` | interactive states, forms, screenshots, mobile emulation, JS-heavy pages |
| `Crawlee` | scalable orchestration, representative-page crawling, retries, queueing |
| `Firecrawl` | quick map + multi-page markdown extraction |
| `Crawl4AI` | open-source structured extraction and clean markdown |
| `Scrapy` | large deterministic crawls and link graphs |
| `ScrapeGraphAI` | optional AI extraction or entity enrichment |

## Audit modes

### Quick audit

Use when the goal is triage.

- small marketing site
- limited time
- low need for screenshots

Typical stack: `Firecrawl` or `Crawl4AI`

### Evidence audit

Default mode for business websites.

- combines crawl and browser inspection
- includes screenshots
- checks key interaction states

Typical stack: `Firecrawl` or `Crawl4AI` + `Playwright`

### Large-site audit

Use for catalogs, directories, media, or documentation portals.

- map first
- classify templates
- audit representative pages

Typical stack: `Scrapy` or `Crawlee` + `Playwright`

## Working artifacts

The skill should create:

- an evidence file using `references/evidence-template.md`
- a final report using `references/report-template.md`

The evidence file exists to preserve honesty:

- what was directly observed
- what was extracted
- what was inferred
- what could not be verified

## Built-in safeguards

1. **Evidence honesty**
   Never claim that an element is absent when it may simply be hidden behind interaction or not captured by the crawler.

2. **Severity calibration**
   CRITICAL findings must truly block conversion or trust, not merely be inconvenient.

3. **Confidence labeling**
   Every finding gets High, Medium, or Low confidence.

4. **No fabricated statistics**
   Do not invent percentages or studies to make the report sound stronger.

5. **Template-aware coverage**
   Large sites are sampled by page type, not judged from the homepage alone.

## Example prompts

- `Audit this site: example.com`
- `Review the UX of this landing page and focus on forms`
- `Why is this site not converting?`
- `Check the mobile UX on example.com`
- `Compare this site with 3 competitors`
- `Turn the audit into a fix spec for design and development`

## Installation

Place the `ux-audit` folder in your Codex or Claude skills directory.

## Notes

- This skill is most valuable when the agent has access to both crawl tools and browser automation.
- If only crawl tools are available, the skill should explicitly downgrade confidence on interaction-heavy findings.


-----------------------------------------------------------------------------
RUS
# UX-аудит

Гибридный навык UX-аудита для сайтов. Он объединяет результаты обхода сайта, взаимодействие через браузер и визуальные доказательства, чтобы подготовить бизнес-ориентированный отчет с приоритизированными выводами и практическими рекомендациями.

Эта версия создана для снижения количества ложных пропусков, характерных для аудита только по текстовому обходу, и делает проверку более доказательной за счет скриншотов, уровней уверенности и явного отслеживания доказательств.

## Что делает навык

Навык проверяет сайт по шести блокам:

1. Эвристики Нильсена
2. Конверсия
3. Контент
4. Техническое и визуальное качество
5. Информационная архитектура
6. Быстрая проверка доступности

Поддерживаются:

* быстрые аудиты небольших сайтов
* аудиты с большим количеством доказательств для коммерческих лендингов и сайтов услуг
* аудиты крупных сайтов на основе выборки шаблонов страниц
* сравнение с конкурентами
* спецификации исправлений для внедрения

## Почему эта версия сильнее

По сравнению с рабочим процессом, основанным только на текстовом обходе, эта версия добавляет:

* выбор движка под тип задачи
* явное картирование сайта перед оценкой
* браузерные проверки форм, меню и мобильных состояний
* скриншоты в качестве доказательств
* выборку шаблонов страниц для крупных сайтов
* уровни уверенности для каждого вывода
* отдельный артефакт с доказательствами, чтобы отделять факты от выводов
* быструю проверку доступности по умолчанию

## Рекомендуемые роли инструментов

| Инструмент      | Лучшее применение                                                                     |
| --------------- | ------------------------------------------------------------------------------------- |
| `Playwright`    | интерактивные состояния, формы, скриншоты, мобильная эмуляция, страницы с активным JS |
| `Crawlee`       | масштабируемая оркестрация, обход репрезентативных страниц, повторы, очереди          |
| `Firecrawl`     | быстрое построение карты сайта + извлечение markdown по нескольким страницам          |
| `Crawl4AI`      | open-source структурированное извлечение и чистый markdown                            |
| `Scrapy`        | крупные детерминированные обходы и графы ссылок                                       |
| `ScrapeGraphAI` | опциональное AI-извлечение или обогащение сущностей                                   |

## Режимы аудита

### Быстрый аудит

Используется, когда цель — первичная диагностика.

* небольшой маркетинговый сайт
* ограниченное время
* низкая потребность в скриншотах

Типичный стек: `Firecrawl` или `Crawl4AI`

### Доказательный аудит

Режим по умолчанию для бизнес-сайтов.

* объединяет обход сайта и браузерную проверку
* включает скриншоты
* проверяет ключевые интерактивные состояния

Типичный стек: `Firecrawl` или `Crawl4AI` + `Playwright`

### Аудит крупного сайта

Используется для каталогов, директорий, медиа или документационных порталов.

* сначала строится карта сайта
* классифицируются шаблоны
* проверяются репрезентативные страницы

Типичный стек: `Scrapy` или `Crawlee` + `Playwright`

## Рабочие артефакты

Навык должен создавать:

* файл доказательств на основе `references/evidence-template.md`
* финальный отчет на основе `references/report-template.md`

Файл доказательств нужен для сохранения честности:

* что было непосредственно замечено
* что было извлечено
* что было выведено как предположение
* что не удалось проверить

## Встроенные защитные правила

1. **Честность доказательств**
   Никогда не утверждать, что элемент отсутствует, если он может быть просто скрыт за взаимодействием или не попал в данные обходчика.

2. **Калибровка серьезности**
   Критические выводы действительно должны блокировать конверсию или доверие, а не просто быть неудобными.

3. **Маркировка уверенности**
   Каждый вывод получает уровень уверенности: высокий, средний или низкий.

4. **Без выдуманной статистики**
   Не придумывать проценты или исследования, чтобы отчет звучал убедительнее.

5. **Учет шаблонов страниц**
   Крупные сайты проверяются по типам страниц, а не оцениваются только по главной странице.

## Примеры запросов

* `Проведи аудит этого сайта: example.com`
* `Проверь UX этого лендинга и сфокусируйся на формах`
* `Почему этот сайт плохо конвертирует?`
* `Проверь мобильный UX на example.com`
* `Сравни этот сайт с 3 конкурентами`
* `Преврати аудит в спецификацию исправлений для дизайна и разработки`

## Установка

Поместите папку `ux-audit` в директорию навыков Codex или Claude.

## Примечания

* Этот навык наиболее полезен, когда у агента есть доступ и к инструментам обхода сайта, и к браузерной автоматизации.
* Если доступны только инструменты обхода, навык должен явно снижать уверенность по выводам, связанным с интерактивными элементами.

