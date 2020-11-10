# CHANGELOG для 2.0.x

## Новое
- **[Action]** В абстрактный класс `Lemurro\Api\Core\Abstracts\Action` добавлено свойство `$this->datetimenow`.
- **[Auth]** При вводе кода для входа добавлена проверка на IP-адрес.
- **[CORS]** Добавлен новый конфиг `cors.yaml`.
- **[DataChangeLog]** Добавлены константы для часто используемых действий:
  - `insert` => `$data_change_log::ACTION_INSERT`
  - `update` => `$data_change_log::ACTION_UPDATE`
  - `delete` => `$data_change_log::ACTION_DELETE`
- **[JS-Helpers]** Добавлен хелпер `lemurro.tabs.getTabTitle`.
- **[JS-Библиотеки]** Для валидации форм установлена библиотека [jQuery Validation Plugin](https://github.com/jquery-validation/jquery-validation), которая использовалась ранее, но была удалена в версии Metronic 7.0+.
- **[LoggerFactory]** Добавлен необязательный параметр `channel_name`.
- **[ResponseException]** Добавлен класс `Lemurro\Api\Core\Exception\ResponseException` расширяется от класса `RuntimeException` ловится в ядре и превращается в `Response::exception($e)`.
- **[Roles]** Добавлена возможность указывать css-классы `js-role__PAGENAME--any`, показывает элемент при любом праве доступа в разделе.
- **[Users]** Добавлено новое системное поле `email`.

## Изменено
- **[App]** Файл `lemurro-cron.php` переименован в `cron.php`.
- **[Auth]** По умолчанию регистрация новых пользователей выключена.
- **[Checker]** Проверка на права доступа теперь бросает исключение `ResponseException` при ошибке.
- **[Configs]** Все настройки по умолчанию теперь хранятся в ядре, а в приложении вы можете их переопределить.
- **[Console]** Отказ от инициализации БД в конструкторе, в метод `getDIC` необходимо передать параметр `string $path_root`.
- **[Controller]** В абстрактном классе `Lemurro\Api\Core\Abstracts\Controller` метод `start` должен возвращать экземпляр класса `Symfony\Component\HttpFoundation\Response`.
- **[Core]** В конструктор добавлен обязательный параметр `string $path_root`.
- **[Core]** Вместо `Exception` при отлове ошибок теперь используется `Throwable`.
- **[Core]** При добавлении\сохранении справочника, добавлении\сохранении пользователя, добавлении\сохранении набора прав доступа, применении фильтра в разделе "Пользователи" в контроллеры уходит параметр `json`, содержащий json-строку, вместо параметра `data`.
- **[DB]** Класс `DB::init()` поменялся на `Database`.
- **[File]** Метод `FileInfo::getOne` теперь возвращает `object` или `null`.
- **[Jobby]** В конструктор добавлен параметр `string $path_root`.
- **[JS-библиотеки]** Обновлены до актуальных версий следующие библиотеки:
  - `bowser` до версии `2.10+`
  - `localforage` до версии `1.8+`
- **[JS-Tabs]** Исправлена ошибка с показом табов если есть вложенные табы.
- **[JS-библиотека: SweetAlert2]** В новой версии библиотеки вместо вызова `swal()` необходимо использовать вызов `Swal.fire()`.
- **[LoggerFactory]** Не рекомендуется использовать напрямую, вместо этого есть элемент в DIC `$this->dic['logfactory']`.
- **[Mailer]** Конструктор вместо переменных `string $header` и `string $footer` теперь принимает переменную `string $template` в которой находится полный шаблон письма: шапка, подвал и переменная `__BODY__`.
- **[PHP-библиотеки]** Обновлены до актуальных версий следующие библиотеки:
  - `hellogerard/jobby` до версии `3.5+`
  - `monolog/monolog` до версии `2.1+`
  - `nesbot/carbon` до версии `2.37+`
  - `symfony/*` до версии `5.1+`
- **[Response]** Метод `Response::errorToException` теперь бросает `ResponseException` вместо `RuntimeException`.
- **[Users]** На вкладке `Ключи доступа` изменена вёрстка и добавлено сообщение об отсутствии ключей
- **[Template7 Helper]** Хелпер `lemurrodecimal` выполняет перед выводом `value.toFixed(precision)`, чтобы все цифры были в едином стиле (вместо `123.5` теперь будет `123.50`, при `precision = 2`)

## Устарело
- **[Configs]** Удалена настройка `database.need_connect`.
- **[Database]** Библиотека `j4mie/idiorm` перестала развиваться, будущее у неё туманное, поэтому переходим на `illuminate/database`.
- **[DIC]** Удалён элемент `$this->dic['checker']` вместо него свойство `$this->checker` в абстрактных классах `Lemurro\Api\Core\Abstracts\Controller` и `Lemurro\Api\Core\Helpers\File\FileChecker`.
- **[File]** Удалён метод `FileInfo::getOneORM`.
- **[Mobile]** Остановлена разработка пакетов `client-framework7` и `client-framework7-core-frontend`. В планах сделать мобильную версию без привязки к `Cordova` и возможностью подключить мобильную версию к `Cordova` или сделать `PWA`.
- **[Other]** Удалена ловушка для js-ошибок, генерировала очень высокую нагрузку в проектах с большим количеством пользователей и ошибками в консоли.
- **[Response]** Удалён ранее устаревший метод `errors`.
- **[Route]** Удалён GET-маршрут `/users`.