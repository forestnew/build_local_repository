# Скрипт для автоматизации сборки локального репозитория

Данный скрипт автоматизирует сборку локального репозитория с пакетами (и их зависимостями) для Ubuntu и RedOS (в теории и на других подобных системах).

Локальный репозиторий необходим для установки в закрытом контуре основного разрабатываемого ПО (используется в работе).

## Функции скрипта:

1. Собирает список необходимых пакетов, указанных в определенном репозитории.
2. Собирает информацию на отдельной, "чистой" ВМ: о зависимых пакетах, версию пакета, информацию из какого репозитория будет скачен пакет.
3. Скачивает определенную версию собранных пакетов в предыдущих пунктах.
4. Архивирует и отправляет на основную машину (на которой запущен скрипт).
5. Собирает локальный репозиторий с использованием утилиты `reprepro` (должна быть установлена).
6. Сохраняет txt файл с содержанием информации о каждом используемом пакете (репозиторий из которого был получен, версия, имя, md5sum и пр.).

## Используемые аргументы:

- `--os_name`: Для какой ОС собирать зависимости?
- `--release_name`: Версия ОС, которая будет указана в названии файла.
- `--hostname`: Хост ВМ, на которой будет произведена сборка.
- `--username`: Логин для ВМ.
- `--password`: Пароль для ВМ.
- `--git_link`: Ссылка на репозиторий, где указаны необходимые пакеты.
- `--prepare-repo`: Установит пакет `reprepro`.

## Пример использования:

При запуске скрипта необходимо указать для какой ОС собирать пакеты и данные для ВМ, на которой будут собираться пакеты.

- `--release-name`: необходимо указать для Debian и Ubuntu (например: `bionic`).
- `--note`: указывается для более удобного названия полученных файлов (например, `18`. Тогда получим: `depends_ubuntu18.tar.gz`).
- `--git_link`: указан по умолчанию, изменение не требуется.

**ВАЖНО!** Указанная ОС и ВМ должны совпадать.
