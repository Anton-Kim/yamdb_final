[![YaMDB workflow](https://github.com/Anton-Kim/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/Anton-Kim/yamdb_final/actions/workflows/yamdb_workflow.yml)

## 🎷 Проект YaMDb

**YaMDb** - API-сервис для публикации отзывов пользователей на различные произведения.
<br><br>

**Особенности:**

:black_small_square: система регистрации пользователей с JWT-токеном<br>
:black_small_square: различные пользовательские роли: аононим, аутентифицированный пользователь, модератор, администратор<br>
:black_small_square: категории и жанры произведений<br>
:black_small_square: возможность оставлять отзывы с оценками и комментариями пользователей, их редактирование авторами<br><br>

## ⚙ Используемые технологии:

:black_small_square: **Python**<br>
:black_small_square: **Docker**<br>
:black_small_square: **Nginx**<br>
:black_small_square: **Gunicorn**<br>
:black_small_square: **Django**<br>
:black_small_square: **Django Rest Framework**<br>
:black_small_square: **GIT**<br>
:black_small_square: **PostgreSQL**<br><br>

## 📃 Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:Anton-Kim/infra_sp2.git
```
В папке infra создайте файл .env со следующим содержимым:
```
SECRET_KEY=1234567890
DEBUG = False
ALLOWED_HOSTS="*"
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=Qwerty88
DB_HOST=db
DB_PORT=5432
```
Из папки с файлом docker-compose.yaml разверните проект:
```
docker-compose up -d --build
```
Выполните миграции:
```
docker-compose exec web python manage.py migrate
```
Cоздайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Заполните базу начальными данными:
```
docker-compose exec web python manage.py loaddata fixtures.json
```
Соберите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
<br>

## 💻 Примеры запросов:

Получение списка всех произведений:
```
GET http://127.0.0.1:8000/api/v1/titles/

{
    "count": 2,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 1,
            "category": {
                "name": "Музыка",
                "slug": "music"
            },
            "genre": [
                {
                    "name": "Поп-рок",
                    "slug": "pop-rock"
                }
            ],
            "rating": 6,
            "name": "A-Ha - Lifelines",
            "year": 2002,
            "description": "Песня"
        },
        {
            "id": 2,
            "category": {
                "name": "Фильмы",
                "slug": "films"
            },
            "genre": [
                {
                    "name": "Мыло",
                    "slug": "soap"
                }
            ],
            "rating": 4,
            "name": "Санта Барбара",
            "year": 1984,
            "description": ""
        }
    ]
}
```
Полуение отзыва по id:
```
GET http://127.0.0.1:8000/api/v1/titles/1/reviews/4/

{
    "id": 3,
    "author": "leo",
    "text": "Потянет",
    "score": 5,
    "pub_date": "2022-06-17T10:44:44.562182Z"
}
```
Добавление комментария к отзыву:
```
POST http://127.0.0.1:8000/api/v1/titles/1/reviews/4/comments/

{
"text": "Не могу не согласиться"
}
```
<br>

## 👾 Авторы проекта:

### Андреев Антон:
```
e-mail: obsos32@gmail.com
GitHub: github.com/Anton-Kim
```
### Ванеева Светлана:
```
e-mail: karasevalana@gmail.com
GitHub: github.com/Svetlana-coderV
```

### Гисматуллин Эрик:
```
e-mail: gismatullin1803@mail.ru
GitHub: github.com/Erik180
```