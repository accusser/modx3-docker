# MODX 3 Docker Environment

Docker-окружение для MODX Revolution 3 с PHP 8.4, MySQL 8.0 и Nginx.

## Требования

- Docker
- Docker Compose

## Быстрый старт

### 1. Клонируйте репозиторий

```bash
git clone https://github.com/accusser/modx3-docker.git
cd modx3-docker
```

### 2. Создайте файл окружения

```bash
cp .env.example .env
```

При необходимости измените пароли в `.env`.

### 3. Скачайте MODX 3

Скачайте MODX 3 с официального сайта: https://modx.com/download

Распакуйте архив в папку `www/`.

### 4. Запустите контейнеры

```bash
docker-compose up -d --build
```

### 5. Установите MODX

Откройте в браузере: http://localhost:8080/setup/

**Данные для подключения к БД:**

| Параметр | Значение |
|----------|----------|
| Host | `mysql` |
| Database | `modx` |
| User | `modx` |
| Password | `modxpassword` |

## Сервисы

| Сервис | URL |
|--------|-----|
| MODX (сайт) | http://localhost:8080 |
| MODX (админка) | http://localhost:8080/manager/ |
| phpMyAdmin | http://localhost:8081 |
| MySQL | localhost:3306 |

## Структура проекта

```
.
├── docker-compose.yml
├── .env.example
├── www/                    # Сюда распаковать MODX
└── docker/
    ├── php/
    │   ├── Dockerfile      # PHP 8.4-fpm
    │   └── php.ini
    └── nginx/
        └── default.conf
```

## Команды

```bash
# Запуск
docker-compose up -d

# Остановка
docker-compose down

# Просмотр логов
docker-compose logs -f

# Пересборка PHP-контейнера
docker-compose up -d --build php

# Вход в PHP-контейнер
docker exec -it modx3-php bash
```

## PHP расширения

- pdo_mysql
- gd (с поддержкой jpeg, png, webp)
- mbstring
- xml
- zip
- intl
- opcache
- exif

## Лицензия

MIT
