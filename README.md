# API Ya Muddle Doodle Base
## api_yamdb

![example workflow](https://github.com/AntonDMoskalev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
### Технологии:
[![Python](https://img.shields.io/badge/-Python-464646?style=flat-square&logo=Python)](https://www.python.org/) [![Django](https://img.shields.io/badge/-Django-464646?style=flat-square&logo=Django)](https://www.djangoproject.com/) [![Django REST Framework](https://img.shields.io/badge/-Django%20REST%20Framework-464646?style=flat-square&logo=Django%20REST%20Framework)](https://www.django-rest-framework.org/) [![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat-square&logo=PostgreSQL)](https://www.postgresql.org/) [![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat-square&logo=NGINX)](https://nginx.org/ru/) [![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat-square&logo=gunicorn)](https://gunicorn.org/) [![docker](https://img.shields.io/badge/-Docker-464646?style=flat-square&logo=docker)](https://www.docker.com/) [![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat-square&logo=GitHub%20actions)](https://github.com/features/actions) [![Yandex.Cloud](https://img.shields.io/badge/-Yandex.Cloud-464646?style=flat-square&logo=Yandex.Cloud)](https://cloud.yandex.ru/)

### Описание проекта:
#### Проект API системы сбора отзывов и на различные произведения (кино, музыка, фильмы, книги, картины да всё что угодно) Проект позволяет публиковать отзывы к различным произведениям и выставлять им оценки, также пользователи могут комментировать опубликованные отзывы. Данный проект поможет людям делится собственным мнением, и помочь пользователям определится с тем хотят ли они тратить время на знакомство с каким-либо произведением. Создателям произведений так же будет интересно узнать об оценке их творчества. Всё это позволит не только найти друзей с общими интересами, но повысить планку качества для авторов любых произведений.


### Запуск проекта на сервере:

#### Склонировать репозиторий
> https://github.com/AntonDMoskalev/yamdb_final.git

### Подготовка сервера:

#### Обновить индекс пакетов APT
>sudo apt update 

#### Обновите установленные в системе пакеты и установите обновления безопасности
>sudo apt upgrade -y

#### Установить менеджер пакетов pip, утилиту для создания виртуального окружения venv, систему контроля версий git, чтобы клонировать ваш проект.
>sudo apt install python3-pip python3-venv git -y

#### Установите на свой сервер Docker
>sudo apt install docker.io

#### Установите docker-compose
>sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

>sudo chmod +x /usr/local/bin/docker-compose

#### Загрузите файлы docker-compose.yaml и nginx.conf на удалённый сервер.
>scp /mnt/c/<Путь к проекту>/nginx/default.conf  <login>@<IP>:/home/<Имя>
>scp /mnt/c/<Путь к проекту>/docker-compose.yaml  <login>@<IP>:/home/<Имя>

#### Добавьте в Secrets GitHub переменные окружения:
>DB_ENGINE=<django.db.backends.postgresql>
>DB_NAME=<имя базы данных postgres>
>DB_USER=<пользователь бд>
>DB_PASSWORD=<пароль>
>DB_HOST=<db>
>DB_PORT=<5432>

>DOCKER_PASSWORD=<пароль от DockerHub>
>DOCKER_USERNAME=<имя пользователя>

>DJANGO_SK=<секретный ключ проекта django>

>USER=<username для подключения к серверу>
>HOST=<IP сервера>
>PASSPHRASE=<пароль для сервера, если он установлен>
>SSH_KEY=<ваш SSH ключ (для получения команда: cat ~/.ssh/id_rsa)>(Копировать полностью)

### Workflow состоит из трёх шагов:
##### Тестирование проекта.
##### Сборка и публикация образа.
##### Автоматический деплой на сервер.

#### Собрать контейнеры на удалённом сервере
>sudo docker-compose up -d --build

#### Выполнить миграции, собрать статику, создать суперпользователя(По необходимости)
>sudo docker-compose exec backend python manage.py migrate

>sudo docker-compose exec backend python manage.py collectstatic

>sudo docker-compose exec backend python manage.py createsuperuser
