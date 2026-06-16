# Localizator

Компонент MODX Revolution для мультиязычных сайтов без контекстов: языковые версии и отдельные домены, перевод полей ресурса (включая SEO и TV), автоперевод лексиконов.

**Текущая версия:** 1.1.1-beta

**Документация:** [docs.modx.pro/components/localizator](https://docs.modx.pro/components/localizator/)

## Возможности

- Псевдоконтексты локализации (`site.ru/en/`, отдельные домены и т.п.)
- Перевод стандартных полей ресурса, SEO и TV (TV с чекбоксом «Доступен в локализациях»)
- Автоматический перевод через Yandex, Google, DeepL или копирование без API
- Массовый автоперевод лексиконов в менеджере
- Интеграция с pdoTools (pdoResources, pdoMenu, pdoPage) и mSearch2 / mFilter2
- Корректный вывод локализованных TV в Fenom (с 1.1.0)

## Требования

- MODX Revolution 2.x, PHP 7.4+, включённые ЧПУ (friendly URLs)
- [pdoTools](https://modx.pro/extras/773), [MIGX](https://modx.pro/extras/176)
- MySQL 5.7+ или MySQL 8+ (исправления совместимости с MySQL 8 — в 1.1.1)

Установка через [modstore.pro](https://modstore.pro/packages/ecommerce/localizator).

## Документация

Полное руководство на [docs.modx.pro](https://docs.modx.pro/components/localizator/):

| Раздел | Ссылка |
|--------|--------|
| Обзор | [Localizator](https://docs.modx.pro/components/localizator/) |
| Быстрый старт | [quick-start](https://docs.modx.pro/components/localizator/quick-start) |
| Системные настройки | [settings](https://docs.modx.pro/components/localizator/settings) |
| Сниппет `Localizator` | [snippet-localizator](https://docs.modx.pro/components/localizator/snippet-localizator) |
| Переключение языков (`getLocales`) | [switch-languages](https://docs.modx.pro/components/localizator/switch-languages) |
| События плагина | [events](https://docs.modx.pro/components/localizator/events) |
| Атрибут hreflang | [hreflang-attribute](https://docs.modx.pro/components/localizator/hreflang-attribute) |

Changelog в репозитории: [core/components/localizator/docs/changelog.txt](core/components/localizator/docs/changelog.txt).

Для выборки локализованных ресурсов через pdoTools укажите в системных настройках:

```
pdoFetch.class = pdotools.pdofetchlocalizator
```

Подробнее: [Системные настройки](https://docs.modx.pro/components/localizator/settings).

## Быстрый старт

Пошаговое подключение — в [документации](https://docs.modx.pro/components/localizator/quick-start). Краткие примеры:

### Меню с учётом локализации

```fenom
{'!Localizator' | snippet : [
  'snippet' => 'pdoMenu',
  'parents' => 0,
  'level' => 2,
  'tplOuter' => '@INLINE {$wrapper}'
]}
```

### Список переведённых документов

```fenom
<ul>
{'!Localizator' | snippet : [
  'snippet' => 'pdoResources',
  'parents' => 4,
  'tpl' => '@INLINE <li><a href="{$uri}">{$pagetitle}</a></li>'
]}
</ul>
```

### Переключатель языков

```fenom
{'!getLocales' | snippet}
```

Кастомная разметка — [Переключение языков](https://docs.modx.pro/components/localizator/switch-languages).

### Локализованные поля в шаблоне

```fenom
<h1>{$_modx->resource.longtitle ?: $_modx->resource.pagetitle}</h1>
<p>{$_modx->resource.localizator_content}</p>
```

Модификатор Fenom `locfield` — [Сниппет Localizator](https://docs.modx.pro/components/localizator/snippet-localizator).

## Что нового в 1.1.1-beta

- **MySQL 8:** исправлена сортировка категорий TV в форме локализации (зарезервированное слово `rank`)
- **Лексиконы:** массовый автоперевод больше не останавливается на первом уже существующем переводе ([#9](https://github.com/modx-pro/localizator/issues/9))

Подробнее — в [changelog](core/components/localizator/docs/changelog.txt).

## Репозиторий и поддержка

- GitHub: [modx-pro/localizator](https://github.com/modx-pro/localizator)
- Issues: [github.com/modx-pro/localizator/issues](https://github.com/modx-pro/localizator/issues)
- Документация: [docs.modx.pro/components/localizator](https://docs.modx.pro/components/localizator/)
- Оригинальный форк: [nizart91/localizator](https://github.com/nizart91/localizator)

Автор компонента: but1head ([radionov@me.com](mailto:radionov@me.com))
