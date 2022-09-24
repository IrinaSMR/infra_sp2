## API_YAMDB
***
### Описание проекта:

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий может быть расширен.

***
### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/IrinaSMR/infra_sp2.git
cd infra_sp2
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv или python3 -m venv venv для Linux
source venv/Scripts/activate или source venv/bin/activate для Linux
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
cd api_yamdb
pip install -r requirements.txt
```

Перейти в папку с файлом docker-compose.yaml:

```
cd infra
```

Поднять контейнеры (infra_db_1, infra_web_1, infra_nginx_1):

```
docker-compose up -d --build
```

Выполнить миграции:

```
docker-compose exec web python manage.py migrate
```

Создать суперпользователя (указать имя, адрес эл.почты, пароль):

```
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Создать дамп базы данных:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остановить контейнеры:

```
docker-compose down -v
```

### Шаблон наполнения файла .env:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres1
DB_HOST=db
DB_PORT=5432
```

## Примеры использования api:

Получение произведений:

```
GET /api/v1/titles/
```

Добавление произведения (только администратор):

```
POST /api/v1/titles/
```

В параметрах передавать json:

```
{
    "name": "Название произведения",
    "year": 1990,
    "description": "Описание произведения",
    "genre": [
    "fantasy"
    ],
    "category": "films"
}
```

***
## Документация API YaMDb

Документация доступна по эндпойнту: http://localhost/redoc/

## Author
- IrinaSMR
