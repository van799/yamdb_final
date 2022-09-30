# yamdb_final
![yamdb_final](https://github.com/van799/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### Краткое описание проекта YaMDb!!!!

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». В каждой категории есть произведения: книги, фильмы или музыка. Произведению может быть присвоен жанр. Новые жанры может создавать только администратор. Пользователи могут оставить к произведениям текстовые отзывы и поставить произведению оценку в диапазоне от одного до десяти. Из пользовательских оценок формируется усреднённая оценка произведения — рейтинг. Присутствует возможность комментирования отзывов.

### Адрес сайтаa 
http://178.154.221.41/redoc/

### Шаблон наполнения env-файла

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```


### Запуск контейнера и приложения в нем

1. Перейти в репозиторий для запуска докера

```
cd infra/
```

2. Запуск docker-compose

```
docker-compose up -d --build
```

3. Выполните следующие команды для базы данных, создайте супер пользователя, соберите статик файлы
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```

4. Войдите в админку под своим логином и создайте одну-две записи объектов


### Для создания дампа (резервную копию) базы данных используйте следующую команду:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

### Загрузите данные из fixtures в БД!
```
python manage.py loaddata fixtures.json
```

### Примеры запросов

#### Получение списка всех произведений:
**GET _/api/v1/titles/_**

*Пример ответа:*
```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "name": "string",
        "slug": "string"
      }
    ]
  }
]
```

#### Добавление произведения:
**POST _/api/v1/titles/_**
```
{
  "name": "string",
  "year": 0,
  "description": "string",
  "genre": [
    "string"
  ],
  "category": "string"
}
```


### Автор:
> - Дмитриев Алексей 