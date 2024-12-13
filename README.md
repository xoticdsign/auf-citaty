# returnauf

**!!! Я прекрасно понимаю, что нельзя так хранить .env, но считаю, что в рамках данного проекта это уместно, так как его основные задачи - демонстрация и локальное использование.** 

**returnauf** — это юмористический проект, демонстрирующий использование различных технологий в реальных условиях. Приложение представляет собой API для работы с коллекцией цитат. Оно разработано с использованием высокопроизводительных инструментов и лучших практик, включая кэширование, логирование и масштабируемую архитектуру.

### Структура проекта

```bash
returnauf/
├── cmd/
│   └── app/
│       └── main.go
├── config/
│   └── config.go
├── docs/
│   ├── docs.go
│   ├── swagger.json
│   └── swagger.yaml
├── internal/
│   ├── app/
│   │   └── app.go
│   ├── cache/
│   │   ├── cache.go
│   │   └── cache_test.go
│   ├── middleware/
│   │   ├── middleware.go
│   │   └── middleware_test.go
│   ├── database/
│   │   ├── database.go
│   │   └── database_test.go
│   ├── handlers/
│   │   ├── handlers.go
│   │   └── handlers_test.go
│   ├── logging/
│   │   └── logging.go
│   └── utils/
│       ├── utils.go
│       └── utils_test.go
├── models/
│   └── responses/
│       └── responses.go
├── .dockerignore
├── .env
├── .gitignore
├── db.sqlite
├── compose.yaml
├── Dockerfile
├── go.mod
└── go.sum
```

### Используемые технологии

- **Go**  
  Основной язык разработки.

- **Fiber**  
  Обрабатывает маршруты, запросы и ответы. Поддерживает Middleware для проверки аутентификации и логирования.

- **SQLite**    
  Легковесная база данных, используемая для хранения цитат.

- **Redis**  
  Используется для кэширования данных, что ускоряет доступ к часто запрашиваемым цитатам.

- **Zap**  
  Применяется для отслеживания ошибок, предупреждений и информационных сообщений.

- **Swagger**  
  Используется для документации.

- **Docker**  
  Используется для контейнеризации приложения. Обеспечивает переносимость. Упрощает развертывание в разных средах.

### Unit и Integration-тестирование  

Используются библиотеки **testify** и встроенные инструменты Golang для покрытие тестами ключевых функций проекта. Тесты проверяют корректность работы маршрутов, API-ключей и вспомогательных методов..

### Архитектурный паттерн

Приложение **returnauf** разработано в рамках **12-факторной архитектуры**, что обеспечивает:
- Простоту конфигурации через переменные среды.
- Легкость масштабирования.
- Возможность развертывания в облачных средах.

### Тип API

**returnauf - это REST API**, которое:
- Обрабатывает HTTP-запросы для работы с данными.
- Возвращает ответы в формате JSON.

## Действия

Ниже описаны доступные маршруты и примеры запросов.

### Маршруты:

```bash
GET /           # Возвращает полный список цитат
GET /random     # Возвращает случайную цитату
GET /:id        # Возвращает цитату по заданному ID
```

### Сделать запрос к API

```bash
curl http://localhost:8080/<маршрут>?returnauf-key=<ключ>
```

## Как установить и использовать?

**returnauf** можно запустить двумя способами: в Docker-контейнере или локально.

### Запуск с использованием Docker

1. Убедитесь, что у вас установлен **Docker**.

2. Клонируйте репозиторий:
  
```bash
git clone github.com/xoticdsign/returnauf
```

```bash
cd returnauf   
```

3. Запустите приложение с помощью Docker Compose:

```bash
docker-compose up --build
```

4. Приложение будет доступно по адресу:
   
```bash
http://localhost:8080
```

### Локальный запуск

1. Убедитесь, что у вас установлены:

- **Go (версия 1.23 или выше)**
- **Redis**

2. Клонируйте репозиторий:

```bash
git clone github.com/xoticdsign/returnauf
```

```bash
cd returnauf
```

3. Установите зависимости:

```bash
go mod download
```
   
4. Убедитесь, что **Redis** работает локально (по умолчанию на localhost:6379).

5. Запустите приложение:

```bash
go run cmd/app/main.go
```
   
6. Приложение будет доступно по адресу:

```bash
http://localhost:8080
```

### Переменные окружения

В файле .env находятся ключевые настройки для работы приложения.

Пример конфигурации:

```env
SERVER_ADDRESS=0.0.0.0:8080
REDIS_ADDRESS=127.0.0.1:6379
REDIS_PASSWORD=""
DB_ADDRESS=db.sqlite
API_KEY=testKey
```

## Тестирование

Для запуска тестов выполните:

```bash
go test ./...
```

## Лицензия

[MIT](https://mit-license.org/)
