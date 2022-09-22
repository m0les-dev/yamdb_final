![example workflow](https://github.com/m0les-dev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# API для сервиса YAMDB

**YAMDB**  собирает отзывы пользователей на произведения.

При разработке приложения использованы фреймфорки `django и django-rest-framework`. В качестве базы выступает `postgresql`
Запуск проекта осуществляется средствами `docker`

## Установка

#### 1. Установка docker и docker-compose

Если у вас уже установлены docker и docker-compose, этот шаг можно пропустить, иначе можно воспользоваться официальной [инструкцией](https://docs.docker.com/engine/install/).

#### 2. Клонируйте репозиторий на локальный компьютер
```bash
git clone git@github.com:DUProkofev/infra_sp2.git
```

#### 3. Настройки перед запуском
Перейдите в директорию infra
```bash
cd infra_sp2/infra/
```
Выполните команды в соответствии с описанием
```bash
touch .env
echo DB_NAME=postgres>>.env # или придумайте другое
echo POSTGRES_USER=postgres>>.env # или придумайте другое
echo POSTGRES_PASSWORD='<придумайте пароль для пользоваетля БД>'>>.env
echo DB_HOST=db>>.env
echo DB_PORT=5432>>.env
echo SECRET_KEY = '<секретный ключ проекта>'>>.env
echo ALLOWED_HOSTS = '<добавьте разрешенные хосты по шаблону хост1, хост2, ..., хостN>'>>.env
echo DEBUG = '<Режим дебага (True or False)>'>>.env
```

#### 4. Запуск контейнеров
```bash
docker-compose up -d
```

#### 5. Команды для работы с контейнерами
```bash
docker-compose start # запуск контейнеров
docker-compose stop # остановить контейнеры
```

#### 5. Настройки приложения Django
```bash
docker-compose exec web python manage.py migrate # выполните миграции
docker-compose exec web python manage.py createsuperuser # создание суперпользователя
```

#### Пример инициализации стартовых данных:
```bash
docker-compose run web python manage.py loaddata fixtures.json
```

#### Работа с api
Документация ко всем эндпоинтам описана в [redoc](localhost/redoc/)

## Основные использованные технологии
* python
* [django](https://www.djangoproject.com/)
* [drf](https://www.django-rest-framework.org/)
* [posgresql](https://www.postgresql.org/)
* [docker](https://www.docker.com/)

## Авторы
* https://github.com/m0les-dev 
