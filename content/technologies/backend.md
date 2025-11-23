+++
weight = 2
title = 'Backend'
+++

# Backend

Этот документ посвящён необходимым знаниям, относящихся к Go Backend, напрямую или косвенно.

## Общие знания

Владение общими знаниями хорошо тем, что они применимы к любой Backend платформе, будь то Java, .Net, NodeJS или другие.

### Клиент-серверное взаимодействие, IP адреса, DNS

Базовые идеи, о которых необходимо иметь общее представление. Что нужно знать:
- Что такое IP адрес
- Разница между TCP и UDP
- Что такое TCP сокет
- Клиент-серверное взаимодействие. Что именно происходит, когда браузер запрашивает страницу сайта
- Что такое DNS

#### Избранные курсы и учебные ресурсы

- [Основы Backend](https://www.youtube.com/watch?v=9rpgE3nZb94) от Сергея Жукова, по основам бэкенда и истории развития бэкенд и веб приложений
- [Написание Go Api](https://www.youtube.com/watch?v=rCJvW2xgnk0&list=PLFAQFisfyqlXBCswWt7jpa1HJep-SiQQr) написание api на практике
- [Как работает DNS]((https://www.youtube.com/watch?v=JZ_JZikhqcg)) от VladTen, как работает DNS
- [Курс по компьютерным сетя]((https://www.youtube.com/watch?v=wq-6a1vzyb8&list=PLd7QXkfmSY7aiCeQDZ7y9AO9NZUpLdhC)) сложный курс из итмо по компьютерным сетям
- [MDN How does the Internet work](https://developer.mozilla.org/ru/docs/Learn/Common_questions/How_does_the_Internet_work)
- [MDN How the Web works](https://developer.mozilla.org/ru/docs/Learn/Getting_started_with_the_web/How_the_Web_works)

### HTTP

Главный протокол WEB.

Что нужно знать:
- HTTP методы
- Заголовки, cookies
- Коды ответа
- Form data, multipart form data

#### Избранные курсы и учебные ресурсы

- [Статья](https://zametkinapolyah.ru/servera-i-protokoly/chto-nuzhno-znat-pro-http-protokol-veb-razrabotchiku-pravila-http-protokola.html) про HTTP простым языком
- [Моя лекция](https://www.youtube.com/watch?v=yWzesBoTOvE) по HTTP, API, REST
- Практика - проекты, начиная с 3

## Авторизация

При авторизации пользователя, бэкенд приложению необходимо авторизовывать запросы, и понимать, кто их делает. Например, при загрузке страницы личного кабинета, неавторизованному пользователю будет отказано в доступе, а авторизованному - показана его личная информация.

Для реализации этого на практике используется 2 основных идеи и способов "привязки" сессии текущего пользователя к клиентам (обычно, браузерам). Идеи:
- Сессии
- JWT

Способы привязки:
- Cookies
- HTTP заголовки

### Сессии

Классическая реализация:
- Сессия генерируется при авторизации, сохраняется в БД (колонки - id, user id), ID сессии устанавливается клиенту через куку
- При каждом запросе клиент отправляет куку, бэкенд приложение ищет сессию в БД по ID из куки, и определяет, какой пользователь сделал запрос

### JWT

JWT расшифровывается как Json Web Token. Информация о сессии целиком хранится внутри токена. При генерации токена он подписывается секретным ключом, который знает только бэкенд приложение, что позволяет защититься от его подделки.

Основное преимущество - JWT токены не хранятся со стороны бэкенда, а передаются целиком при каждом запросе.

#### Избранные курсы и учебные ресурсы

- Ключевые отличия сессий от JWT, плюсы и минусы каждого варианта - [https://stytch.com/blog/jwts-vs-sessions-which-is-right-for-you/](https://stytch.com/blog/jwts-vs-sessions-which-is-right-for-you/)
- Куки - [https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
- Сессии - [https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Sessions](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Sessions)
- JWT:
  - [https://jwt.io/introduction](https://jwt.io/introduction)
  - Интеграция JWT с Go 
    - Николай Тузов [https://www.youtube.com/watch?v=EURjTg5fw-E](https://www.youtube.com/watch?v=EURjTg5fw-E)
    - Максим Жашкевич [https://www.youtube.com/watch?v=EURjTg5fw-E](https://www.youtube.com/watch?v=EURjTg5fw-E)
- Практика - проекты #5 ["Погода"](../projects/weather-viewer.md) и #6 ["Облачное хранилище файлов"](../projects/cloud-file-storage.md) (сессии), #7 ["Планировщик задач"](../projects/task-tracker.md) - JWT

## REST API

REST - набор правил взаимодействия клиента и сервера на основе HTTP. Сделать работающее клиент-серверное приложение легко, элегантно его спроектировать - сложно. 

Что нужно знать:
- Отличие RESTful от RESTless
- Базовые дизайн принципы и типовые ошибки, которых следует избегать

#### Избранные курсы и учебные ресурсы

- Статьи по REST на хабре - [#1](https://habr.com/ru/post/483202/), [#2](https://habr.com/ru/post/351890/)
- [Моя лекция](https://www.youtube.com/watch?v=yWzesBoTOvE) по HTTP, API, REST
- Книга по дизайну REST API - [https://www.amazon.com/REST-Design-Rulebook-Mark-Masse/dp/1449310508](https://www.amazon.com/REST-Design-Rulebook-Mark-Masse/dp/1449310508)
- Практика - проекты #3 ["Обмен валют"](../projects/currency-exchange.md) и #7 ["Планировщик задач"](../projects/task-tracker.md) содержат примеры дизайна REST API

## Go

Перейдём к знаниям, относящимся напрямую к Backend разработке на Go.

### Go HTTP

Необходимо изучить, как в go происходит обработка http запросов и документацию http библиотеки.

Что нужно уметь:
- Писать обработчики запросов с помощь stdlib ["Документация"](https://pkg.go.dev/net/http) и использование mux ["Документация"](https://pkg.go.dev/net/http@master#ServeMux)

#### Избранные курсы и учебные ресурсы

- Николай Тузов [Написание простого http api на go](https://www.youtube.com/watch?v=rCJvW2xgnk0&list=PLFAQFisfyqlXBCswWt7jpa1HJep-SiQQr)
- Практика - проекты с 3 по 4

### Frameworks

В Go нет единого доминирующего фреймворка, как, например, Spring в Java. Вместо этого экосистема предлагает множество лёгких и специализированных библиотек - особенно для маршрутизации, - а базовый функционал веб-приложений (роутинг, middleware, обработка запросов/ответов и пр.) часто собирается из отдельных компонентов под конкретные задачи.

Что нужно уметь:

- Работать с middleware
- Работать с context
- Уметь правильно составлять зависимости между компонентами приложений

#### Избранные курсы и учебные ресурсы

- Примеры таких библиотек:
  - [Echo](https://github.com/labstack/echo)
  - [Fiber](https://github.com/gofiber/fiber)
  - [Gin](https://github.com/gin-gonic/gin)
- Практика - проекты с 5 по 7

### Шаблонизаторы веб-страниц

Шаблонизатор - это механизм генерации HTML-разметки с динамическим содержимым. Типичный сценарий: встраивание данных из БД (например, списка постов или профиля пользователя) в заранее подготовленную HTML-структуру. 

 Go предоставляет встроенные пакеты text/template и html/template. Они компилируют шаблоны в AST и обеспечивают безопасную (с автоматическим экранированием) подстановку данных - без необходимости подключать сторонние зависимости. 

Что нужно уметь:
- Передавать данные из Go в шаблон
  
#### Избранные курсы и учебные ресурсы

- [Статья](https://habr.com/ru/articles/792802/) статья с хабра с базовым обзором
- [Документация](https://pkg.go.dev/text/template)
- Практика - проекты 5

## Что дальше

Перечисленные выше знания и инструменты - база для Java Junior. Если есть желание и необходимость углубиться в Backend технологии, советую обратить внимание на:
- Websocket
- XML, Protobuf
- Альтернативны REST - SOAP, GRPC, GraphQL
- Очереди сообщений