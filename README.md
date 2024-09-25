# Tourist Agency Database

## Обзор

Эта база данных предназначена для управления информацией для туристического агентства. Она состоит из 11 таблиц, в которых хранятся данные о гидах, странах, турах, клиентах, отзывах, экскурсиях, контрактах, посещенных экскурсиях, бронированиях, туристах и туристах по бронированию.

## Tables:

### Гид (Guides)
- Фамилия (Last Name)
- Имя (First Name)
- Отчество (Patronymic)
- Телефон (Phone)
- Электронная_почта (Email)
- Стаж (Experience)
- ID_GID (Primary Key)

### Страна (Countries)
- ID_Country (Primary Key)
- Название_страны (Country Name)

### Туры (Tours)
- Название (Tour Name)
- Описание (Tour Description)
- Цена (Tour Price)
- Дата_начала (Tour Start Date)
- Дата_окончания (Tour End Date)
- ID_Country (Foreign Key referencing Страна)
- ID_TUR (Primary Key)

### Клиенты (Clients)
- Фамилия (Last Name)
- Имя (First Name)
- Отчество (Patronymic)
- Телефон (Phone)
- Электронная_почта (Email)
- Страна (Country)
- Город (City)
- Адрес_проживания (Address)
- ID_Country (Foreign Key referencing Страна)
- Id_client (Primary Key)

### Отзывы (Reviews)
- Оценка (Rating)
- Комментарии (Comments)
- Дата_добавления (Review Date)
- Дата_изменения (Review Update Date)
- Id_client (Foreign Key referencing Клиенты)
- ID_exc (Foreign Key referencing Экскурсия)

### Экскурсия (Excursions)
- ID_exc (Primary Key)
- Название (Excursion Name)
- Описание (Excursion Description)
- Длительность (Excursion Duration)
- Стоимость_для_фирмы (Excursion Cost for Company)
- ID_GID (Foreign Key referencing Гид)
- ID_Country (Foreign Key referencing Страна)

### Договор (Contracts)
- Дата_заключения_договора (Contract Date)
- ID_TUR (Foreign Key referencing Туры)
- id_dog (Primary Key)

### Посещенные_экскурсии (Visited Excursions)
- Стоимость_для_клиента (Excursion Cost for Client)
- Дата_посещения (Visit Date)
- ID_exc (Foreign Key referencing Экскурсия)
- id_dog (Foreign Key referencing Договор)

### Бронирование (Bookings)
- ID_bron (Primary Key)
- Дата_бронирования (Booking Date)
- Количество_туристов (Number of Tourists)
- Сумма_оплаты (Payment Amount)
- Дата_оплаты (Payment Date)
- Id_client (Foreign Key referencing Клиенты)

### Туристы (Tourists)
- Id_client (Foreign Key referencing Клиенты)
- id_dog (Foreign Key referencing Договор)

### Туристы_по_броне (Tourists by Booking)
- ID_bron (Foreign Key referencing Бронирование)
- id_dog (Foreign Key referencing Договор)

## Relationships
Связи между таблицами устанавливаются с помощью внешних ключей:

Тур связан со страной (Туры -> Страна)

Клиент связан со страной (Ссылки -> Страна)

Отзыв связан с клиентом и экскурсией (Отзывы -> Ссылки, Отзывы -> Экскурсия)

Экскурсия ассоциируется с гидом и страной (Экскурсия -> Гидия, Экскурсия -> Страна).

С туром связан контракт (Договор -> Туры)

Посещение экскурсии связано с контрактом и самой экскурсией (Приглашенные_экскурсии -> Разговор, Посещенные_экскурсии -> Экскурсия)

Бронирование связано с клиентом (Бронирование -> Ссылки) Турист связан с клиентом и контрактом (Туры -> Клиенты, Туры -> Консультант)

Турист посредством бронирования связан с бронированием и контрактом (Туристы_по_броне -> Бронирование, Туристы_по_броне -> Договор)

## Usage
Эта база данных может использоваться для управления информацией о турах, клиентах, экскурсиях, отзывах, гидах, контрактах, посещенных экскурсиях, бронированиях, туристах и самих туристах при бронировании в туристическом агентстве.
