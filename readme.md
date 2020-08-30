
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

## Список сервисов

* bitrix_mysql - сервис с БД в качестве СУБД используется MariaDB [образ](https://hub.docker.com/repository/docker/alex19pov31/bitrix-mariadb) построен на базе alpine
* bitrix_nginx - официальный [образ](https://hub.docker.com/_/nginx) nginx на базе alpine
* bitrix_memcached - официальный [образ](https://hub.docker.com/_/memcached) memcached на базе alpine
* bitrix_php56-fpm - [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php56-fpm) с php 5.6 на базе официального образа [php](https://hub.docker.com/_/php)
* bitrix_php71-fpm - [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php71-fpm) с php 7.1 на базе официального образа [php](https://hub.docker.com/_/php)
* bitrix_php72-fpm - [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php72-fpm) с php 7.2 на базе официального образа [php](https://hub.docker.com/_/php)
* bitrix_php73-fpm - [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php73-fpm) с php 7.3 на базе официального образа [php](https://hub.docker.com/_/php)
* bitrix_php74-fpm - [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php74-fpm) с php 7.4 на базе официального образа [php](https://hub.docker.com/_/php)
* bitrix_php8-fpm - **В настоящий момент данная версия не поддреживается bitrix** [сервис](https://hub.docker.com/repository/docker/alex19pov31/bitrix-php8-fpm) с php 8 на базе официального образа [php](https://hub.docker.com/_/php)

## Настройка

Перед запуском необходимо создать конфигурационный файл .docker/.env в котором будет указан пароль для root пользователя к mysql:

```
# Пример содержимого конфигурационного файла
MYSQL_ROOT_PASSWORD=123456
TERM=dumb
```

По-умолчанию данная сборка ищет проекты в родительской директории (на уровень выше файла docker-compose.yml). Идентификация проекта построена через веб-сервер (nginx) название директории проекта должно соответствовать одному из перечисленных шаблонов:

* *.p56 - проекты на php 5.6 (пример someproject.p56)
* *.p71 - проекты на php 7.1 (пример someproject.p71)
* *.p72 - проекты на php 7.2 (пример someproject.p72)
* *.p73 - проекты на php 7.3 (пример someproject.p73)
* *.p74 - проекты на php 7.4 (пример someproject.p74)
* *.p8 - проекты на php 8 (пример someproject.p8)

Доменное имя проекта будет соответсвовать названию директории, все эти настройки можно изменить на свой вкус настройках веб-сервера **.docker/nginx/conf/etc/nginx/conf.d**

## Управление

Управление сборкой происходит из директории с файлом docker-compose. Основные команды:

* docker-compose up -d - сборка и запуск контейнеров
* docker-compose start - запуск ранее собранных контейнеров
* docker-compose stop - остановка контейнеров
* docker-compose rm - удаление остановленных контейнеров
* docker-compose ps - состояние контейнеров