# API Ya Muddle Doodle Base
## api_yamdb

![example workflow](https://github.com/AntonDMoskalev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Проект API системы сбора отзывов и на различные произведения (кино, музыка, фильмы, книги, картины да всё что угодно) Проект позволяет публиковать отзывы к различным произведениям и выставлять им оценки, также пользователи могут комментировать опубликованные отзывы. Данный проект поможет людям делится собственным мнением, и помочь пользователям определится с тем хотят ли они тратить время на знакомство с каким-либо произведением. Создателям произведений так же будет интересно узнать об оценке их творчества. Всё это позволит не только найти друзей с общими интересами, но повысить планку качества для авторов любых произведений. Вместе мы делаем этот мир лучше)

# Установка Docker:

### 1. Для начала запустите команду удаления старых версий Docker. Скорее всего их на вашем компьютере нет, но подстраховаться не помешает:
> sudo apt remove docker docker-engine [docker.io](http://docker.io/) containerd runc

#### Вывод будет примерно таким:
> E: Unable to locate package docker-engine 

### 2. Чтобы устанавливать новые версии пакетов и утилит обновите их список для менеджера пакетов ATP:
> sudo apt update 

### 3. Затем установите пакеты для работы через протокол https, это нужно для получения доступа к репозиторию докера:
> sudo apt install \
  > apt-transport-https \
  > ca-certificates \
  > curl \
  > gnupg-agent \
  > software-properties-common -y 
  
### 4. Добавьте ключ GPG для подтверждения подлинности в процессе установки:
> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

### 5. Добавьте репозиторий Docker в пакеты apt:
> sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

### 6. Так как в APT был добавлен новый репозиторий, снова обновите индекс пакетов:
> sudo apt update

### 7. Установите Docker, а вместе с ним Docker Compose:
> sudo apt install docker-ce docker-compose -y

### 8. Проверьте, что Docker работает:
> sudo systemctl status docker

# Команды для запуска приложения.

### Для запуска проекта выполните команду:
#### docker-compose up -d

#### В результате выполнения команды у вас развернётся проект, запущенный через gunicorn с базой данных postgres.

### Проверить запущенные контейнеры:
> docker container ls

### Запустить контейнер:
> docker container start <CONTAINER ID>
  
### Остановить контейнер:
> docker container stop <CONTAINER ID>
  

# Выполнить миграции, создать суперпользователя и собрать статику:
  
### Выполнить миграции:
> docker-compose exec web python manage.py migrate
  
### Создать суперпользователя:
> docker-compose exec web python manage.py createsuperuser
  
### Собрать статиску:
> docker-compose exec web python manage.py collectstatic --no-input 


# Теперь проект доступен по адресу http://localhost/. При этом номер порта указывать уже не надо: умный nginx принимает запросы на стандартном порте и перенаправляет их в приложение.
=======

### 1. Для начала запустите команду удаления старых версий Docker. Скорее всего их на вашем компьютере нет, но подстраховаться не помешает:
> sudo apt remove docker docker-engine [docker.io](http://docker.io/) containerd runc

#### Вывод будет примерно таким:
> E: Unable to locate package docker-engine 

### 2. Чтобы устанавливать новые версии пакетов и утилит обновите их список для менеджера пакетов ATP:
> sudo apt update 

### 3. Затем установите пакеты для работы через протокол https, это нужно для получения доступа к репозиторию докера:
> sudo apt install \
  > apt-transport-https \
  > ca-certificates \
  > curl \
  > gnupg-agent \
  > software-properties-common -y 
  
### 4. Добавьте ключ GPG для подтверждения подлинности в процессе установки:
> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

### 5. Добавьте репозиторий Docker в пакеты apt:
> sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

### 6. Так как в APT был добавлен новый репозиторий, снова обновите индекс пакетов:
> sudo apt update

### 7. Установите Docker, а вместе с ним Docker Compose:
> sudo apt install docker-ce docker-compose -y

### 8. Проверьте, что Docker работает:
> sudo systemctl status docker

# Команды для запуска приложения.

### Установить переменные окружения в файле .env
#### Указываем базу данных
> DB_ENGINE=
#### Имя базы данных
> DB_NAME=
#### Логин для подключения к базе данных
> POSTGRES_USER=
#### Пароль для подключения к БД
> POSTGRES_PASSWORD=
#### Название сервиса (контейнера)
> DB_HOST=
#### Порт для подключения к БД 
> DB_PORT=

### Для запуска проекта выполните команду:
> docker-compose up

#### В результате выполнения команды у вас развернётся проект, запущенный через gunicorn с базой данных postgres.

### Проверить запущенные контейнеры:
> docker container ls

### Запустить контейнер:
> docker container start <CONTAINER ID>
  
### Остановить контейнер:
> docker container stop <CONTAINER ID>
  

# Выполнить миграции, создать суперпользователя и собрать статику:
  
### Выполнить миграции:
> docker-compose exec web python manage.py migrate
  
### Создать суперпользователя:
> docker-compose exec web python manage.py createsuperuser
  
### Собрать статиску:
> docker-compose exec web python manage.py collectstatic --no-input 


# Теперь проект доступен по адресу http://178.154.227.92/
