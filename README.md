
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
cd api_yamdb
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv или python3 -m venv venv для Linux
source venv/Scripts/activate или source venv/bin/activate для Linux
python -m pip install --upgrade pip
```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Переходим в папку с файлом docker-compose.yaml:

```
cd infra
```

Поднимаем контейнеры (infra_db_1, infra_web_1, infra_nginx_1):

```
docker-compose up -d --build
```

Выполнить миграции:

```
docker-compose exec web python manage.py migrate
```

Создать суперпользователя (указываем имя, адрес эл.почты, пароль):

```
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Создать дамп базы данных (нет в текущем репозитории):

```
docker-compose exec web python manage.py dumpdata > dumpPostrgeSQL.json
```

Остановить контейнеры:

```
docker-compose down -v
```

***
## Документация API YaMDb

Документация доступна по эндпойнту: http://localhost/redoc/

## Author
- IrinaSMR
