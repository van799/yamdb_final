# api_yamdb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles).

### Описание
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
### Установка
Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:e-pakhomov/api_yamdb.git
cd api_yamdb
```
Cоздать и активировать виртуальное окружение:

<sub>для Windows 10:</sub>
```
python -m venv venv
. venv/Scripts/activate
```
Установить зависимости из файла requirements.txt:
```
python -m pip install --upgrade pip
pip install -r requirements.txt
```
Перейти в репозиторий api:
```
cd api_yamdb
```
Выполнить миграции:
```
python manage.py migrate
```
Запустить проект:
```
python manage.py runserver
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
*Пример ответа:*
```
{
  "id": 0,
  "name": "string",
  "year": 0,
  "rating": 0,
  "description": "string",
  "genre": [
    {
      "name": "string",
      "slug": "string"
    }
  ],
  "category": {
    "name": "string",
    "slug": "string"
  }
}
```

#### Добавление нового отзыва:
**POST _/api/v1/titles/{title_id}/reviews/_**
```
{
  "text": "string",
  "score": 1
}
```
*Пример ответа:*
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```

#### Добавление комментария к отзыву:
**POST _/api/v1/titles/{title_id}/reviews/{review_id}/comments_**
```
{
  "text": "string"
}
```
*Пример ответа:*
```
{
  "id": 0,
  "text": "string",
  "author": "string",
  "pub_date": "2019-08-24T14:15:22Z"
}
```

### Авторы:
> - Евгений Пахомов 
> - Яна Луканова 
> - Алексей Дмитриев
