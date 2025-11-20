# vedear-mermaid
mermaid test

# Уровень 1
## Задание 1.1
```mermaid
    flowchart TD
    A[Запустить Steam] --> B[Найти игру в Магазине]
    B --> C{Игра есть в наличии?}
    C -- Да --> D[Добавить в корзину и оплатить]
    C -- Нет --> B
    D --> E[Скачать и установить игру]
    E --> F[Наслаждаться игрой!]
```

## Задание 1.2

```mermaid
sequenceDiagram
    Повар->>Ингредиенты: Смешать
    Повар->>Духовка: Выпекать
    Духовка-->>Повар: Готово
    Повар->>Торт: Украсить
```
# Уровень 2
## Задание 2.1

```mermaid
classDiagram
    class Book {
        -String title
        -String author
        -String ISBN
        -boolean isAvailable
        +checkOut()
        +returnBook()
        +getBookInfo()
    }

    class User {
        -String name
        -String userId
        -List~Book~ borrowedBooks
        +borrowBook(Book)
        +returnBook(Book)
        +getBorrowedBooks()
    }

    class Library {
        -List~Book~ books
        -List~User~ users
        +addBook(Book)
        +removeBook(Book)
        +registerUser(User)
        +findBook(String) Book
        +lendBook(User, Book)
    }

    User "*" -- "*" Book : borrows
    Library "1" *-- "*" Book : contains
    Library "1" *-- "*" User : manages
```

## Задание 2.2

```mermaid
gantt
    title Детальная диаграмма Ганта: Разработка мобильного приложения
    dateFormat  YYYY-MM-DD
    axisFormat  %d/%m

    section Планирование
    Анализ требований      :crit, req_analysis, 2024-01-01, 3d
    Техническое проектирование :tech_design, after req_analysis, 2d

    section Разработка
    Дизайн UI/UX          :design, after tech_design, 7d
    Фронтенд-разработка   :frontend, after design, 10d
    Бэкенд-разработка     :backend, after tech_design, 12d

    section Тестирование
    Интеграционное тестирование :integration_test, after frontend backend, 3d
    Функциональное тестирование :func_test, after integration_test, 2d
    Релиз                :release, after func_test, 1d
```
# Уровень 3
## Задание 3.1

```mermaid
graph TB
    subgraph Frontend
        A[React] --> B[Redux]
        A --> C[Router]
        B --> C
    end

    subgraph Backend
        D[Node.js] --> E[Express]
        E --> F[MongoDB]
    end

    subgraph ExternalServices
        G[Stripe<br/>Платежи]
        H[SendGrid<br/>Email]
    end

    %% Связи между компонентами
    C --> E
    E --> G
    E --> H
    E --> A

    %% Стилизация
    style Frontend fill:#808080
    style Backend fill:#808080
    style ExternalServices fill:#808080
    style A fill:#4fc3f7
    style D fill:#81c784
    style G fill:#800000
    style H fill:#800000
```

## Задание 3.2

```mermaid
stateDiagram-v2
    [*] --> Новый

    state "Оплата" as payment_process {
        [*] --> Ожидание_оплаты
        Ожидание_оплаты --> Оплата_обрабатывается : платеж отправлен
        Оплата_обрабатывается --> Оплаченный : подтверждение банка
        Оплата_обрабатывается --> Ошибка_оплаты : отказ банка
        Ошибка_оплаты --> Ожидание_оплаты : повторная попытка
        Ошибка_оплаты --> Отмененный : превышены попытки
    }

    state "Доставка" as delivery {
        [*] --> Упаковка
        Упаковка --> Готов_к_отправке
        Готов_к_отправке --> В_пути
        В_пути --> Доставлен_в_пункт_выдачи
        В_пути --> Доставлен_курьером
        Доставлен_в_пункт_выдачи --> Получен
        Доставлен_курьером --> Получен
    }

    Новый --> Ожидание_оплаты : клиент подтвердил
    Новый --> Отмененный : клиент отменил

    Оплаченный --> Упаковка
    Получен --> Доставленный
    Доставленный --> Возвращенный : клиент вернул товар
    Доставленный --> [*] : успешное завершение

    Отмененный --> [*]
    Возвращенный --> [*]
```
# Уровень 4
## Задание 4.1

```mermaid
journey
    title Детальная карта пути: Покупка билетов в кино
    section Поиск фильма
      Открытие приложения: 5: Воодушевление
      Просмотр новых фильмов: 5: Интерес
      Чтение описаний и отзывов: 4: Любопытство
      Выбор фильма: 4: Предвкушение
    section Выбор сеанса
      Выбор удобной даты: 4: Удовлетворение
      Поиск подходящего времени: 3: Нетерпение
      Проверка наличия мест: 3: Обеспокоенность
    section Выбор мест
      Просмотр схемы зала: 4: Вовлеченность
      Поиск лучших мест: 4: Энтузиазм
      Быстрый выбор: 5: Радость
      Подтверждение: 4: Уверенность
    section Оплата
      Ввод платежных данных: 2: Напряжение
      Ожидание подтверждения: 3: Тревога
      Успешная оплата: 5: Облегчение
    section Получение билетов
      Мгновенное получение: 5: Восторг
      Проверка на email: 4: Спокойствие
      Планирование похода: 4: Предвкушение
```

## Задание 4.2

```mermaid
erDiagram
    USER {
        int user_id PK "Автоинкремент"
        string username "Уникальный"
        string email "Уникальный"
        string password_hash
        string profile_picture "NULL"
        datetime created_at
        datetime updated_at
    }

    POST {
        int post_id PK "Автоинкремент"
        int author_id FK
        string content "Текст поста"
        string image_url "NULL"
        datetime created_at
        datetime updated_at
        boolean is_published
    }

    COMMENT {
        int comment_id PK "Автоинкремент"
        int post_id FK
        int author_id FK
        int parent_comment_id FK "NULL"
        string content
        datetime created_at
        datetime updated_at
    }

    LIKE {
        int user_id FK
        int post_id FK
        datetime created_at
    }

    FOLLOW {
        int follower_id FK
        int following_id FK
        datetime created_at
    }

    USER ||--o{ POST : "author"
    USER ||--o{ COMMENT : "author"
    USER ||--o{ LIKE : "user"
    POST ||--o{ COMMENT : "post"
    POST ||--o{ LIKE : "post"
    USER ||--o{ FOLLOW : "follower"
    FOLLOW }o--|| USER : "following"
```

## Задание 5

```mermaid
flowchart TD
    A[Клиент открывает приложение] --> B[Выбор ресторана и блюд]
    B --> C{Проверка доступности}
    C -- Доступно --> D[Оформление заказа]
    C -- Не доступно --> B
    D --> E[Оплата заказа]
    E --> F[Ресторан получает заказ]
    F --> G[Приготовление еды]
    G --> H[Курьер забирает заказ]
    H --> I[Доставка клиенту]
    I --> J[Получение и оценка]
    J --> K[Завершение заказа]
```
```mermaid
sequenceDiagram
    participant К as Клиент
    participant С as Сервер
    participant Р as Ресторан
    participant Кур as Курьер

    К->>С: Поиск ресторана и выбор блюд
    С->>Р: Проверка доступности
    Р-->>С: Подтверждение
    С-->>К: Доступно для заказа

    К->>С: Оформление и оплата
    С->>Р: Новый заказ
    Р->>Р: Приготовление еды
    Р-->>С: Заказ готов

    С->>Кур: Назначение доставки
    Кур->>Р: Забрать заказ
    Кур->>К: Доставить заказ
    К-->>С: Подтверждение получения
    К-->>С: Оценка сервиса
```
```mermaid
classDiagram
    class User {
        -String userId
        -String name
        -String phone
        -String address
        +register()
        +login()
        +placeOrder()
    }

    class Restaurant {
        -String restaurantId
        -String name
        -String address
        -String cuisine
        +addMenuItem()
        +updateAvailability()
        +receiveOrder()
    }

    class MenuItem {
        -String itemId
        -String name
        -String description
        -double price
        -boolean available
    }

    class Order {
        -String orderId
        -Date orderDate
        -String status
        -double totalAmount
        +calculateTotal()
        +updateStatus()
    }

    class Courier {
        -String courierId
        -String name
        -String vehicle
        -String status
        +acceptOrder()
        +updateLocation()
        +completeDelivery()
    }

    User "1" -- "*" Order : places
    Restaurant "1" -- "*" MenuItem : has
    Restaurant "1" -- "*" Order : receives
    Order "*" -- "*" MenuItem : contains
    Courier "1" -- "*" Order : delivers
```
```mermaid
erDiagram
    USERS {
        int user_id PK
        varchar name
        varchar email
        varchar phone
        varchar address
        datetime created_at
    }

    RESTAURANTS {
        int restaurant_id PK
        varchar name
        varchar address
        varchar cuisine_type
        varchar phone
        boolean is_active
    }

    MENU_ITEMS {
        int item_id PK
        int restaurant_id FK
        varchar name
        text description
        decimal price
        boolean is_available
    }

    ORDERS {
        int order_id PK
        int user_id FK
        int restaurant_id FK
        int courier_id FK
        decimal total_amount
        varchar status
        datetime order_time
        datetime delivery_time
    }

    ORDER_ITEMS {
        int order_id FK
        int item_id FK
        int quantity
        decimal price
    }

    COURIERS {
        int courier_id PK
        varchar name
        varchar phone
        varchar vehicle_type
        boolean is_available
    }

    REVIEWS {
        int review_id PK
        int order_id FK
        int rating
        text comment
        datetime created_at
    }

    USERS ||--o{ ORDERS : places
    RESTAURANTS ||--o{ MENU_ITEMS : offers
    RESTAURANTS ||--o{ ORDERS : receives
    ORDERS ||--o{ ORDER_ITEMS : contains
    MENU_ITEMS ||--o{ ORDER_ITEMS : included_in
    COURIERS ||--o{ ORDERS : delivers
    ORDERS ||--|| REVIEWS : has
```
```mermaid
journey
    title User Journey: Заказ доставки еды
    section Поиск и выбор
      Открытие приложения: 5: Интерес
      Поиск ресторана: 4: Любопытство
      Просмотр меню: 5: Предвкушение
      Выбор блюд: 4: Удовлетворение
    section Оформление заказа
      Заполнение данных: 3: Нетерпение
      Выбор способа оплаты: 4: Уверенность
      Подтверждение заказа: 5: Радость
    section Ожидание доставки
      Отслеживание статуса: 4: Вовлеченность
      Ожидание курьера: 3: Нетерпение
    section Получение заказа
      Встреча с курьером: 4: Облегчение
      Проверка заказа: 4: Внимательность
      Оценка сервиса: 5: Завершенность
```
```mermaid
gantt
    title План разработки Сервиса доставки еды
    dateFormat YYYY-MM-DD
    axisFormat %d/%m

    section Анализ и проектирование
      Сбор требований     :crit, req, 2024-01-01, 10d
      Проектирование архитектуры :design, after req, 14d
      Создание макетов UI   :ui_design, after req, 12d

    section Бэкенд разработка
      База данных и API    :backend, after design, 21d
      Система оплаты       :payment, after backend, 14d
      Интеграция с картами :maps, after backend, 10d

    section Фронтенд разработка
      Клиентское приложение :frontend, after ui_design, 28d
      Панель ресторана     :restaurant_ui, after ui_design, 21d
      Приложение курьера   :courier_ui, after ui_design, 18d

    section Тестирование
      Модульное тестирование :unit_test, after backend, 14d
      Интеграционное тестирование :integration, after frontend, 21d
      User Acceptance Testing :uat, after integration, 14d

    section Запуск
      Деплой и настройка   :deploy, after uat, 7d
      Запуск в продакшен   :launch, after deploy, 1d
```

## Задание 6

```mermaid
pie title Рынок автомобилей в России (примерные данные на 2024 год)
    "Иномарки" : 45
    "Отечественные" : 25
    "Совместное производство" : 30
```