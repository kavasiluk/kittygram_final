![GitHub Action Status](https://github.com/kavasiluk/kittygram_final/actions/workflows/main.yml/badge.svg)



![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)

# Kittygram

Проект-блог для размещения информации о своих кошках, выполненный в рамках учебного курса Yandex Practicum.

## Запуск проекта из образов с Docker hub

Для запуска необходимо создать папку проекта, например `kittygram` и перейти в нее:

```bash
mkdir kittygram
cd kittygram
```

В папку проекта скачиваем файл `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up
```

Произойдет скачивание образов, создание и включение контейнеров, создание томов и сети.

## Запуск проекта из исходников GitHub

Клонируем себе репозиторий: 

```bash 
git clone git@github.com:kavasiluk/kittygram_final.git
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up
```

## После запуска: Миграции, сбор статистики

После запуска необходимо выполнить сбор статистики и миграции бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /static/static/
```

И далее проект доступен на: 

```
http://localhost:9000/
```

## Памятка о том, как заполнять .env файл

Для корректной работы проекта Kittygram необходимо заполнить файл `.env` следующим образом:

dotenv
POSTGRES_DB=django
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
Debug=False
ALLOWED_HOSTS=your.ip,your.domain,localhost,127.0.0.1
USE_SQLITE=False

 Перед запуском проекта убедитесь, что переменные окружения в файле .env заполнены корректно и соответствуют вашей конфигурации базы данных.

## Авторы

Konstantin Vasiluk
Tg: @Derot23
Git: https://github.com/kavasiluk
