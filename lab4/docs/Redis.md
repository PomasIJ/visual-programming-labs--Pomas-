# Redis в n8n

## Способ установки

В задании предлагалось установить Redis через Docker. Так как Docker на
моём компьютере не работает (конфликт виртуализации с VMware, ошибка
0x80073712), я использовал облачный Redis от Upstash (бесплатный тариф,
без карты).

## Данные подключения

- **Host**: `polished-lynx-139684.upstash.io`
- **Port**: `6379`
- **TLS**: ✅
- **Password**: (хранится в credentials n8n)

## Реализованные workflows

### Workflow 1: создание и чтение ключа

1.  Manual Trigger.
2.  Redis (Set) — ключ `shilo`, значение «Это тестовое значение».
3.  Redis (Get) — читает ключ `shilo`.

**Скриншот:** `../screenshots/9redis.png`

### Workflow 2: удаление и проверка

1.  Manual Trigger.
2.  Redis (Delete) — удаляет ключ `shilo`.
3.  Redis (Get) — проверяет, что ключа нет (возвращает `null`).

**Скриншот:** `../screenshots/10redis.png`

## Вывод

Redis в n8n используется через ноду `Redis`. Она поддерживает все
основные операции: Set, Get, Delete, Exists, а также pub/sub. Облачный
Redis от Upstash полностью заменил локальный Docker-контейнер.
