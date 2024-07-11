# Bang-Gong - браузерная и мобильная игра

## Описание:
Bang-Gong - браузерная и мобильная игра, являющаяся адаптацией популярной настольной игры Bang! Проект разработан с использованием GoLang, Redis, Postgres и React

## Цель проекта:
Демонстрация навыков изучения языка GoLang и создание увлекательной онлайн-игры

## Структура
- Серверная часть:
  - Разделение на сервисы: 
    - БД (Postgres) - хранит данные, которые не часто меняются
    - Кэш (Redis) - хранит данные, которые часто меняются
    - Игровой Контроллер (Go) - управляет игровым процессом
    - АПИ (Go) - предоставляет доступ для клиентов (создает комнаты, принимает ходы и т.д.)
  - Использование Docker-compose для запуска сервисов
- Клиентская часть:
  - Сайт модерации (nginx/react)
  - Сайт игры (nginx/react)
  - Мобильное приложение (Go)
  - Документация к АПИ (Swagger-UI)
- Игровой процесс:
  - Игра реализована на основе классических правил Bang!
  - Игроки могут создавать комнаты и приглашать друзей, а также играть со случайными противниками
  - Все роли, персонажи и карты хода раздаются случайно
  - Игровой процесс управляется сервисом "Игровой Контроллер"
  - Данные об игре хранятся в кеше, а после завершения игры - в базе данных
- Размещение:
  - Проект размещается на собственном арендованном сервере

## Используемые технологии:
- [GoLang](https://golang.org/)
- [Redis](https://redis.io/)
- [Postgres](https://www.postgresql.org/)
- [React](https://reactjs.org/)
- [Docker](https://www.docker.com/)
- [Docker-compose](https://docs.docker.com/compose/)
- [Nginx](https://nginx.org/)

## Первый запуск сервера
### Необходимые программы
- [Docker Compose](https://docs.docker.com/compose/install/linux/)
- [NodeJS](https://nodejs.org/en/download/package-manager)
### Настройка окружения:
- Создайте файл .env в корне проекта
- Заполните его следующими переменными:
```env
# Хост
HOST_DOMAIN=localhost

# База данных
DB_USER=admin
DB_PASSWORD=12345
DB_NAME=bang
DB_EXTERNAL_PORT=5432

# Кэш
CACHE_USER=admin
CACHE_USER_PASSWORD=12345
CACHE_PASSWORD=12345
CACHE_EXTERNAL_PORT=6379

# API
API_EXTERNAL_PORT=8000
API_HOST=http://$HOST_DOMAIN:$API_EXTERNAL_PORT

# Browser Client
BROWSER_CLIENT_SERVER_NAME=$HOST_DOMAIN
BROWSER_CLIENT_EXTERNAL_PORT=80

# Moderation Client
MODERATION_CLIENT_SERVER_NAME=$HOST_DOMAIN
MODERATION_CLIENT_EXTERNAL_PORT=81

# Documentantion
DOC_EXTERNAL_PORT=82
DOC_HOST=http://$HOST_DOMAIN:$DOC_EXTERNAL_PORT
```
### Сборка сайта игры и модерации
В папке browser-client/moderation-client запустить
```bash
npm install
npm build
```
### Запуск
В коневой папке проетк запустить
```bash
docker compose up -d
```
## Пололнительные ссылки
- [ARCHITECTURE.md](ARCHITECTURE.md) - файл с описанием архитектуры игры
- [LICENSE](LICENSE.md) - файл с описанием лицензии
- Автор Кологерманский Фёдор:
    - [Телеграмм](https://t.me/kologermit)
    - [VK](https://vk.com/kologermit/)
    - [GitHub](https://github.com/kologermit)
    - [Почта](mailto://kologermit@gmail.com)