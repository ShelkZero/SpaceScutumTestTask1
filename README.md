# Laravel Docker App

Этот проект представляет собой веб-приложение, созданное с использованием Laravel, которое работает в контейнерах Docker. В проекте используется база данных MariaDB, сервер Nginx, а также другие компоненты для обработки и отображения данных.

## Шаг 1: Установка необходимых инструментов

Перед началом работы убедитесь, что на вашем компьютере установлены следующие инструменты:

1. **Docker** — для создания и управления контейнерами приложения и базы данных.  
   [Инструкция по установке Docker](https://docs.docker.com/get-docker/)

2. **Docker Compose** — для упрощения работы с несколькими контейнерами (Laravel, MariaDB, PHP, Nginx).  
   [Инструкция по установке Docker Compose](https://docs.docker.com/compose/install/)

3. **Git** — для клонирования репозитория и управления версиями кода.  
   [Инструкция по установке Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

4. **Composer** — для установки зависимостей Laravel.  
   [Инструкция по установке Composer](https://getcomposer.org/doc/00-intro.md)

5. **Node.js и NPM** — если необходимо работать с фронтендом (для сборки ассетов).  
   [Инструкция по установке Node.js и NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

6. **VS Code или другой редактор кода** — для работы с проектом.  
   [Скачать VS Code](https://code.visualstudio.com/)

## Шаг 2: Настройка проекта Laravel с Docker

1. Клонируйте репозиторий с помощью Git:

    ```bash
    git clone <URL_репозитория>
    cd <папка_с_проектом>
    ```

2. Скопируйте файл `.env.example` в `.env`:

    ```bash
    cp .env.example .env
    ```

3. Проверьте, что файл `.env` настроен для подключения к MariaDB:

    ```env
    DB_CONNECTION=mysql
    DB_HOST=laravel_db
    DB_PORT=3306
    DB_DATABASE=laravel
    DB_USERNAME=laravel_user
    DB_PASSWORD=Ani@233237
    ```

4. Запустите контейнеры с помощью Docker Compose:

    ```bash
    docker-compose up -d
    ```

    Эта команда создаст и запустит все необходимые контейнеры: Laravel, MariaDB, Nginx.

5. Убедитесь, что Laravel работает, открыв браузер и перейдя по адресу:

    ```
    http://localhost:8000
    ```

## Шаг 3: Настройка базы данных MariaDB

1. После того как контейнеры запущены, необходимо выполнить миграции для создания необходимых таблиц в базе данных.

2. Войдите в контейнер с Laravel:

    ```bash
    docker exec -it laravel_app bash
    ```

3. Запустите миграции и сидеры для базы данных:

    ```bash
    php artisan migrate:fresh --seed
    ```

    Эта команда создаст таблицы для пользователей, товаров, комментариев и истории покупок, а также заполнив их начальными данными.

## Шаг 4: Реализация функционала

### Авторизация

Для реализации регистрации и аутентификации можно использовать Laravel Breeze, Fortify или Sanctum. Выберите подходящий пакет и настройте его для вашего приложения.

Пример установки **Laravel Breeze**:

1. Установите Laravel Breeze:

    ```bash
    composer require laravel/breeze --dev
    php artisan breeze:install
    npm install && npm run dev
    php artisan migrate
    ```

2. Это настроит базовую систему аутентификации с возможностью регистрации и входа пользователей.

### Разработка

Теперь, когда проект настроен и база данных мигрирована, можно приступать к разработке дополнительных функций и расширений.

## Шаг 5: Полезные команды Docker

- **Запуск контейнеров в фоновом режиме**:

    ```bash
    docker-compose up -d
    ```

- **Остановка контейнеров**:

    ```bash
    docker-compose down
    ```

- **Перезапуск контейнера**:

    ```bash
    docker restart <container_id>
    ```

- **Вход в контейнер с PHP**:

    ```bash
    docker exec -it laravel_app bash
    ```

- **Просмотр логов контейнера**:

    ```bash
    docker logs <container_id>
    ``
