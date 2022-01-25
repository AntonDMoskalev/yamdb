# API Ya Muddle Doodle Base

![example workflow](https://github.com/AntonDMoskalev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
### Технологии:
[![Python](https://img.shields.io/badge/-Python-464646?style=flat-square&logo=Python)](https://www.python.org/) [![Django](https://img.shields.io/badge/-Django-464646?style=flat-square&logo=Django)](https://www.djangoproject.com/) [![Django REST Framework](https://img.shields.io/badge/-Django%20REST%20Framework-464646?style=flat-square&logo=Django%20REST%20Framework)](https://www.django-rest-framework.org/) [![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat-square&logo=PostgreSQL)](https://www.postgresql.org/) [![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat-square&logo=NGINX)](https://nginx.org/ru/) [![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat-square&logo=gunicorn)](https://gunicorn.org/) [![docker](https://img.shields.io/badge/-Docker-464646?style=flat-square&logo=docker)](https://www.docker.com/) [![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat-square&logo=GitHub%20actions)](https://github.com/features/actions) [![Yandex.Cloud](https://img.shields.io/badge/-Yandex.Cloud-464646?style=flat-square&logo=Yandex.Cloud)](https://cloud.yandex.ru/)

### Описание проекта:
#### Проект API системы сбора отзывов и на различные произведения (кино, музыка, фильмы, книги, картины да всё что угодно) Проект позволяет публиковать отзывы к различным произведениям и выставлять им оценки, также пользователи могут комментировать опубликованные отзывы. Данный проект поможет людям делится собственным мнением, и помочь пользователям определится с тем хотят ли они тратить время на знакомство с каким-либо произведением. Создателям произведений так же будет интересно узнать об оценке их творчества. Всё это позволит не только найти друзей с общими интересами, но повысить планку качества для авторов любых произведений.
 ---------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Локализация:
#### В проекте по умолчанию установлена русская локализация (ru) и все надписи переведны на русский язык. При необходимости вы можете обновить или созадть записи и перевод сообщений используя следующую команду (выоплненяется из директории проекта или директории приложения):

> ~/project_dir> django-admin makemessages -l ru

#### Затем отредактируйте файл сообщения .po расположенный в папке locale каждого приложения следую инсрукциям из официальной документации После создания файла сообщения - и каждый раз, когда вы вносите в него изменения - вам нужно будет скомпилировать его в более эффективную форму для использования для этого используйте команду:

> ~/project_dir> django-admin compilemessages
------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
### Пользовательские роли в проекте:
1. **Аноним
2. **Аутентифицированный пользователь
3. **Модератор
4. **Администратор

**Анонимные пользователи могут:
1. Просматривать, информацию о произведениях;
2. Просматривать, отзывы на произведения;
3. Просматривать комментарии к отзывам;
4. Просматривать все имеющиеся в проекте жанры и категории.

**Аутентифицированные (user) пользователи могут:
1. Получать данные о **своей** учётной записи;
2. Просматривать, публиковать, удалять и редактировать **свои** отзывы (*автор может оставить только один отзыв к конкретному произведению*);
3. Просматривать, информацию о жанрах и категориях;
4. Просматривать, публиковать комментарии от своего имени к отзывам других пользователей *(включая самого себя)*, удалять и редактировать **свои** комментарии;
***Примечание***: Доступ ко всем операциям записи, обновления и удаления доступны только после аутентификации и получения токена.

**Модератор (user) пользователи могут:
1. Просматривать, публиковать, удалять и редактировать **свои** отзывы (*автор может оставить только один отзыв к конкретному произведению*);
2. Удалять и редактировать любые отзывы (*токсичная критика никому не приносит пользы*);
3. Просматривать, информацию о жанрах и категориях;
4. Просматривать, публиковать комментарии от своего имени к отзывам других пользователей *(включая самого себя)*, удалять и редактировать **свои** комментарии;
5. Удалять и редактировать любые комменатрии (*точки зрения могут быть разными, но это не повод переходить на личности*);

**Администратор (admin) может:
1. Получать информацию о пользователях;
2. Создавать пользователей,изменять их данные и удалять из проекта;
3. Так же может дбавлять новые произведения;
4. Добавлять новые жанры и категории.
----------------------------------------------------------------------------------------------------------------------------------------------------------------
### Набор доступных эндпоинтов:
* ```redoc/``` - Подробная документация по работе API.
* ```api/v1/categories/``` - Получение, публикация и удаление категорий (_GET, POST, DELETE_).
* ```api/v1/genres/``` - Получение, публикация и удаление жанров (_GET, POST, DELETE_).
* ```api/v1/titles/``` - Получение и публикация произведения (_GET, POST_).
* ```api/v1/titles/{id}``` - Получение, изменение, удаление произведения с соответствующим **id** (_GET, PUT, PATCH, DELETE_).
* ```api/v1/titles/{title_id}/reviews/``` - Получение отзывов к произведению с соответствующим **title_id** и публикация новых отзывов(_GET, POST_).
* ```api/v1/titles/{title_id}/reviews/{id}/``` - Получение, изменение, удаление отзыва с соответствующим **id** к произведению с соответствующим **title_id** (_GET, PUT, PATCH, DELETE_).
*  ```api/v1/titles/{title_id}/reviews/{review_id}/comments/``` -  Получение комменатриев и публикация нового комментария к отзыву с соответствующим **review_id**, при этом отзыв оставлен к произведению с соответствующим **title_id**(_GET, POST_).
*  ```api/v1/titles/{title_id}/reviews/{review_id}/comments/{id}/``` -  Получение, изменение, удаление комменатрия с соответствующим **id** к отзыву с соответствующим **review_id**, при этом отзыв оставлен к произведению с соответствующим **title_id**(_GET, PUT, PATCH, DELETE_).

* #### Операции с пользователями:
  * ```api/v1/users/``` - получение информации о пользователе и создание новых пользователей. Только **admin** (_GET, POST_). 
  * ```api/v1/users/{username}``` - Получение, изменение, удаление информации о пользователе. Только **admin** (_GET, PUT, PATCH, DELETE_).
  * ```api/v1/users/me/``` - получение и изменение данных своей учётной записи. Доступна любым авторизованными пользователям (_GET, PATCH_). 

* #### Аутентификация и создание новых пользователей:
  * ```api/v1/auth/signup/``` - Регистрация нового пользователя (_POST_). 
  * ```api/v1/auth/token/``` - Получение JWT-токена (_POST_).
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### _Алгоритм регистрации пользователей_:
1. Пользователь отправляет POST-запрос на добавление нового пользователя с параметрами ***email*** и ***username*** на эндпоинт ```/api/v1/auth/signup/```.
2. YaMDB отправляет письмо с кодом подтверждения (***confirmation_code***) на адрес ***email***.
3. Пользователь отправляет POST-запрос с параметрами ***username*** и ***confirmation_code*** на эндпоинт ```/api/v1/auth/token/```, в ответе на запрос ему приходит token (JWT-токен).
4. При желании пользователь отправляет PATCH-запрос на эндпоинт ```/api/v1/users/me/``` и заполняет поля в своём профайле (описание полей — в документации).
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### _Примеры выполнения запросов_:
##### Получаем JWT-токена 
>```api/v1/auth/token/```
>
>Payload
>```json
>{
>"username": "string",
>"confirmation_code": "string"
>}
>```
>Response sample (status code = 200)
>```json
>{
>"token": "string"
>}
>```


##### Получение списка всех произведений 
>```api/v1/titles/```
>
>Response sample (status code = 200)
>```json
>[
>  {
>    "count": 0,
>    "next": "string",
>    "previous": "string",
>    "results": [
>      {
>        "id": 0,
>        "name": "string",
>        "year": 0,
>        "rating": 0,
>        "description": "string",
>        "genre": [
>          {
>            "name": "string",
>            "slug": "string"
>          }
>        ],
>        "category": {
>          "name": "string",
>          "slug": "string"
>        }
>      }
>    ]
>  }
>]
>```


##### Опубликовать новый отзыв. 
(*требуется Аутентификация*)
>```api/v1/titles/{title_id}/reviews/```
>
>Payload
>```json
>{
>"text": "string",
>"score": 1
>}
>```
>Response sample (status code = 201)
>```json
>{
>"id": 0,
>"text": "string",
>"author": "string",
>"score": 1,
>"pub_date": "2019-08-24T14:15:22Z"
>}
>```


##### Отредактировать комментарий к отзыву на произведение. 
(*требуется Аутентификация*)
(*доступно авторам и пользователям с правами админиcтратора и модератора*)
>```api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/```
>
>Payload
>```json
>{
>  "text": "string"
>}
>```
>Response sample (status code = 200)
>```json
>{
>  "id": 0,
>  "text": "string",
>  "author": "string",
>  "pub_date": "2019-08-24T14:15:22Z"
>}
>```


##### Добавление новой категории. 
(*Доступно пользователям с правами админиcтратора*)
>```api/v1/categories/```
>
>Payload
>```json
>{
>  "name": "string",
>  "slug": "string"
>}
>```
>Response sample (status code = 201)
>```json
>{
>"name": "string",
>"slug": "string"
>}
>```
--------------------------------------------------------------------------------------------------------------------------------------------------------------  
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

>DB_NAME = <имя базы данных postgres>

>DB_USER = <пользователь бд>

>DB_PASSWORD = <пароль>

>DB_HOST = <db>

>DB_PORT = <5432>

>DOCKER_PASSWORD = <пароль от DockerHub>

>DOCKER_USERNAME = <имя пользователя>

>DJANGO_SK = <секретный ключ проекта django>

>USER = <username для подключения к серверу>
 
>HOST = <IP сервера>
 
>PASSPHRASE = <пароль для сервера, если он установлен>
 
>SSH_KEY = <ваш SSH ключ (для получения команда: cat ~/.ssh/id_rsa)>(Копировать полностью)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Workflow состоит из трёх шагов:
##### Тестирование проекта.
##### Сборка и публикация образа.
##### Автоматический деплой на сервер.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Собрать контейнеры на удалённом сервере
>sudo docker-compose up -d --build
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Выполнить миграции, собрать статику, создать суперпользователя(По необходимости)
>sudo docker-compose exec backend python manage.py migrate

>sudo docker-compose exec backend python manage.py collectstatic

>sudo docker-compose exec backend python manage.py createsuperuser

