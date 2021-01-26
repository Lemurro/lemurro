# CHANGELOG для 2.1.x

## Новое
- **[Auth]** Повышение безопасности при аутентификации.
- **[Database]** Добавлена возможность выбирать БД проекта `mysql` или `pgsql`.
- **[File]** Проверка `container_type` перед добавлением файла.
- **[JS]** В хелпере `lemurro.tabs.tabInsertEdit` добавлены два опциональных аргумента:
    - `tabFormName` - имя таба с формой или null (тогда будет: tab-form)
    - `tabPrevName` - имя предыдущего таба или null (тогда будет: tab-list)
- **[PHP]** Обновление библиотек до актуальных версий:
    - `illuminate/database`: v8.23;
    - `monolog/monolog`: v2.2;
    - `nesbot/carbon`: v2.43;
    - `phpmailer/phpmailer`: v6.2;
    - `symfony/\*`: v5.2.
- **[Sessions]** Удаление устаревших сессий вынесено в cron-задание (каждый час в 30 минут).
- **[SQL]** Файл `database.sql` переименован в `database.my.sql` и добавлен файл `database.pg.sql`.
- **[SQL]** Настроены уникальные поля:
    - для таблицы `info_users` поле `user_id`
    - для таблицы `users` поле `auth_id`
- **[Tests]** Настройка GitHub Actions для автоматических тестов.

## Изменено
- **[Config]** Исправлена ошибка с именем ключа в настройках `auth.yaml`, параметр `sessions_older_than_hours` переименован в `sessions_older_than_days`.
- **[Config]** Отключен валидатор для блока `database`.
- **[JS]** Исправлена ошибка с подключением библиотеки `Inputmask`.
- **[Routes]** Из методов маршрутов убран OPTIONS за ненадобностью.
- **[SQL]** Для таблицы `data_change_logs` в MySQL изменён движок с `InnoDB` на `ARCHIVE`.
- **[Tests]** Правки в тестах, чтобы не ломать существующие данные.

## Устарело
- **[Composer]** Убраны ненужные полифилы.