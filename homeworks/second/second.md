# Знакомство с Django ORM. Проектируем схему бд.

Во втором домашнем задании тебе предстоит выбрать тему своего проекта, если ты еще не определился, предлагаю реализовать доску обьявлений (подобной Avito).

Для начала я рекомендую подумать над схемой хранения данных своего проекта. Сделать это можно на листочке или восользоваться онлайн сервисами на подобие [dbdiagram.io](https://dbdiagram.io/d). Подумай над тем какие таблицы будут в твоем приложении, какие в этих таблицах будут поля и связи.

После создания схемы бд, можно приступать к написанию моделей. На лекции я рассказывал про модели зачем они нужны и как работают, но на всякий случай оставлю [ссылку](https://docs.djangoproject.com/en/4.0/topics/db/models/) на официальную документацию Django по моделям. Если ты выбрал тему "Доска обьявлений" предлагаю создать такие модели:
1. Расширить модель User из стандартного прложения Django auth, путем добаления своей модели Profile  связи с моделью User связью один-к-одному. Каким еще образом это можно сделать кроме связи один-к-одному, можно прочитать в [этой](https://habr.com/ru/post/313764/) статье. В модели Profile создай несколько дополнительных полей, которые понадобятся для твоего приложения. Для того, чтобы вместе с созданием нового пользователя, создавался и новый профиль к нему, воспользуйся сигналами. Дополнительно просигналы можно почитать [тут](https://docs.djangoproject.com/en/4.0/topics/signals/) и посмотреть в лекции.

2. Добавить модели PostCategory, Post, Comment. Post-модель в которой будут храниться все обьявления, подумай какие поля нужны для обьявления и какого типа они должны быть. PostCategory-категория публикаций, нужна будет для того, чтобы фильтровать публикации по категориям. Comment-комментарии, нужна для того, чтобы пользователи могли оставлять свои комментарии. Какие поля и какого типа должны быть решать тебе, дополнительно приложу [ссылку](https://docs.djangoproject.com/en/4.0/ref/models/fields/), где можно посмотреть все доступные типы полей Django ORM. Не забудь связать модели между собой разными связями, об этом я говорил в лекции, когда например связывал комментарии с публикациями и авторами.

3. Зарегистрируй модели в админке. Как это сделать смотри в лекции. 
После описания своих моделей, нужно создать новую миграцию. 
Делается это простой командой 

[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=python+manage.py+makemigrations+имя_приложения)](https://git.io/typing-svg)

После создания миграций в консоли выйдет примерно подобно сообщение
```
Migrations for 'posts':
  posts/migrations/0001_auto.py:
    - Create model Post
    - Create model Comment
```

Далее тебе нужно будет применить миграции

[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=python+manage.py+migrate)](https://git.io/typing-svg)


После создания новых миграций, а также применения их, можно переходить в админку и попробовать воспользоваться моделями, поиграться с ними. Предварительно нужно будет создать супрепользователя для доступа к админке. Делается это командой:

[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=python+manage.py+createsuperuser)](https://git.io/typing-svg)

Заполни все данные суперпользователя, запускай дев сервер и переходи к админке. Авторизуйся по созданным ранее данным и попробуй поиграться с дминкой, создать несколько публикаций например и т.д.