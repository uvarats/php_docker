# Образ докера для проектов на Symfony

### На борту
1. PHP 8.2
2. Nginx
3. Postgres 15
4. Redis

> При необходимости, в .env можно менять внешние порты для Nginx и PostgreSQL (по умолчанию - 8080 и 5432)

### Инструкция по запуску:

1. Клонируем репозиторий
2. bash ./run.sh -c
3. В папку htdocs помещаем исходный код проекта/клонируем репозиторий. 
4. sudo docker compose build
5. sudo docker compose up -d
