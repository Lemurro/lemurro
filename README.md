# Lemurro

[![PHP version](https://img.shields.io/packagist/php-v/Lemurro/api-core.svg)](https://packagist.org/packages/Lemurro/api-core)
[![License](https://img.shields.io/github/license/Lemurro/api-core.svg)](https://github.com/Lemurro/api-core)

[![Latest Stable Version](https://img.shields.io/packagist/v/Lemurro/api-core.svg)](https://packagist.org/packages/Lemurro/api-core)
[![Latest Stable Version](https://img.shields.io/npm/v/lemurro-client-metronic-core-frontend.svg)](https://www.npmjs.com/package/lemurro-client-metronic-core-frontend)
[![NPM Downloads](https://img.shields.io/npm/dt/lemurro-client-metronic-core-frontend.svg)](https://www.npmjs.com/package/lemurro-client-metronic-core-frontend)
[![NPM Downloads](https://img.shields.io/npm/dm/lemurro-client-metronic-core-frontend.svg)](https://www.npmjs.com/package/lemurro-client-metronic-core-frontend)

Boilerplate для написания небольших CRM-систем, в основном построен на компонентах symfony и дополнительных библиотеках

## Системные требования
- PHP >= 7.4.0
- PHP Extensions
  - fileinfo
  - iconv
  - json
  - mbstring
  - pdo_mysql

## Создание нового проекта
Lemurro использует Composer и NPM для управления зависимостями. Перед использованием Lemurro, убедитесь, что у вас установлен Composer и NPM.

1. Скачайте установщик Lemurro через Composer:
  ```bash
composer global require lemurro/installer
```
2. Поместите в ваши переменные среды путь до каталога с установленными глобально пакетами (если не делали этого ранее), это необходимо для получения доступа к команде `lemurro` отовсюду в командной строке, этот каталог расположен в разных местах в зависимости от вашей операционной системы:
  - **Linux**: $HOME/.config/composer/vendor/bin
  - **macOS**: $HOME/.composer/vendor/bin
  - **Windows**: %USERPROFILE%\AppData\Roaming\Composer\vendor\bin
3. Перейдите в каталог с вашими проектами
  ```bash
cd /etc/www
```
4. Следующая команда создаст новый каталог с именем `mycrm` (в каталоге где мы сейчас находимся) и установит модули, выбранные в процессе интерактивного опроса:
  ```bash
lemurro new mycrm
```
5. После успешного создания проекта можно переходить к настройке (разделы документации):
  - API-Сервер (api) > Настройка > Настройка
  - Клиент Metronic (web) > Настройка > Настройка

## Полный синтаксис команды
```bash
lemurro new mycrm --lv=latest --api --web --skip --silent
```
Обязательные аргументы и опции:
- `lemurro new` - команда создания нового проекта
- `mycrm` - имя (каталог) проекта
- `--lv=latest` - номер версии Lemurro для установки, [полный список версий](https://github.com/Lemurro/api/tags) или слово `latest`, для установки последней стабильной версии

Опции установки отдельных модулей, если опцию не указать модуль не будет установлен:
- `--api` - api-сервер
- `--web` - web-клиент (браузерный клиент, основан на дизайн-шаблоне [Metronic](https://keenthemes.com/metronic))

Не обязательные опции:
- `--skip` - если используется команда отличная от простого `lemurro new mycrm` (с использованием опций), тогда эта опция отключит вопросы о необходимости выбора устанавливаемых модулей и версии Lemurro
- `--silent` - отключает вопрос `Continue installation (y|n)`, который показывается после отображения списка определённых параметров установки (имени проекта, версии Lemurro, списке устанавливаемых модулей)

### Например: `lemurro new mycrm --lv=latest --api --web --skip --silent`
- создаст каталог с именем проекта `mycrm`
- последней стабильной версией Lemurro
- модулями `api-сервер` и `web-клиент`
- не станет останавливаться для подтверждения указанных параметров