## Проект: запуск docker-compose для YaMDb

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) 
может быть расширен администратором (например, можно добавить категорию «Изобразительное 
искусство» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» 
могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — 
песня «Давеча» группы «Насекомые» и вторая сюита Баха.
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», 
«Рок» или «Артхаус»).Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) 
и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских 
оценок формируется усреднённая оценка произведения — рейтинг (целое число). 
На одно произведение пользователь может оставить только один отзыв.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

`https://github.com/AigulParamonova/infra_sp2.git`

`cd infra_sp2`

В корневой директории проекта расположен файл .env.example, в котором описаны примеры переменных и их значений.

Запуск контейнера:

`docker-compose up`

Пересборка контейнера и запуск:

`docker-compose up -d --build`

Заполнение базы данными:

`docker-compose exec web python manage.py makemigrations --noinput`

`docker-compose exec web python manage.py migrate --noinput`

`docker-compose exec web python manage.py createsuperuser`

`docker-compose exec web python manage.py collectstatic --no-input`

Создайте резервную копию БД:

`docker-compose exec web python manage.py dumpdata > fixtures.json`

Документация API YaMDb по адресу:

`http://127.0.0.1:8000/redoc/`

### Технологии:
- Python 3
- Django REST Framework
- Docker
- Nginx
- Git