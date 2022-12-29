# CHANGELOG для 1.11.x

## Новое
- **[Database]** Добавлена библиотека `doctrine/dbal`.
  - Для запросов `doctrine/dbal` и `idiorm` используют одно соединение.
  - В абстрактном классе `\Lemurro\Api\Core\Abstracts\Action` добавлено protected свойство `$this->dbal`.
- **[JS - Helper]** Добавлен новый хелпер `lemurro.helper.integer`.
- **[JS - Helper]** Добавлен новый хелпер `lemurro.helper.digitGroups`.
- **[Middleware]** Появилась возможность выполнять Middleware (промежуточное ПО):
  - Для создания классов расширяйте абстрактный класс: `\Lemurro\Api\Core\Abstracts\Middleware`.
  - Уже создан Middleware для всех запросов: `app/Middlewares/MiddlewareForAll.php`.
  - Для использования Middleware в других маршрутах, добавьте строчку:
    ```yaml
    example-index:
      ...
      defaults:
        middleware: 'Lemurro\Api\App\Middlewares\MiddlewareExampleIndex'
    ```
- **[Psalm]** Добавлен конфиг инструмента статического анализа кода.

## Изменено
- **[Composer]** Все внешние пакеты зафиксированы на версии до 24 февраля 2022.
- **[NPM]** Все внешние пакеты зафиксированы на версии до 24 февраля 2022.

## Устарело
- **[Database]** Настоятельно НЕ рекомендуется использовать `ORM::` (библиотека `j4mie/idiorm`) и как можно скорее перейти на использование `doctrine/dbal`.
