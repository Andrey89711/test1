#Tourist Agency Database

##Обзор

Эта база данных предназначена для управления информацией для туристического агентства. Она состоит из 11 таблиц, в которых хранятся данные о гидах, странах, турах, клиентах, отзывах, экскурсиях, контрактах, посещенных экскурсиях, бронированиях, туристах и туристах по бронированию.

##Tables:

###Гид (Guides)
- Фамилия (Last Name)
- Имя (First Name)
- Отчество (Patronymic)
- Телефон (Phone)
- Электронная_почта (Email)
- Стаж (Experience)
- ID_GID (Primary Key)

###Страна (Countries)
- ID_Country (Primary Key)
- Название_страны (Country Name)

###Туры (Tours)
- Название (Tour Name)
- Описание (Tour Description)
- Цена (Tour Price)
- Дата_начала (Tour Start Date)
- Дата_окончания (Tour End Date)
- ID_Country (Foreign Key referencing Страна)
- ID_TUR (Primary Key)

###Клиенты (Clients)
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

###Отзывы (Reviews)
- Оценка (Rating)
- Комментарии (Comments)
- Дата_добавления (Review Date)
- Дата_изменения (Review Update Date)
- Id_client (Foreign Key referencing Клиенты)
- ID_exc (Foreign Key referencing Экскурсия)

###Экскурсия (Excursions)
- ID_exc (Primary Key)
- Название (Excursion Name)
- Описание (Excursion Description)
- Длительность (Excursion Duration)
- Стоимость_для_фирмы (Excursion Cost for Company)
- ID_GID (Foreign Key referencing Гид)
- ID_Country (Foreign Key referencing Страна)

###Договор (Contracts)
- Дата_заключения_договора (Contract Date)
- ID_TUR (Foreign Key referencing Туры)
- id_dog (Primary Key)

###Посещенные_экскурсии (Visited Excursions)
- Стоимость_для_клиента (Excursion Cost for Client)
- Дата_посещения (Visit Date)
- ID_exc (Foreign Key referencing Экскурсия)
- id_dog (Foreign Key referencing Договор)

###Бронирование (Bookings)
- ID_bron (Primary Key)
- Дата_бронирования (Booking Date)
- Количество_туристов (Number of Tourists)
- Сумма_оплаты (Payment Amount)
- Дата_оплаты (Payment Date)
- Id_client (Foreign Key referencing Клиенты)

###Туристы (Tourists)
- Id_client (Foreign Key referencing Клиенты)
- id_dog (Foreign Key referencing Договор)

###Туристы_по_броне (Tourists by Booking)
- ID_bron (Foreign Key referencing Бронирование)
- id_dog (Foreign Key referencing Договор)

##Relationships
Связи между таблицами устанавливаются с помощью внешних ключей:

A tour is associated with a country (Туры -> Страна)
A client is associated with a country (Клиенты -> Страна)
A review is associated with a client and an excursion (Отзывы -> Клиенты, Отзывы -> Экскурсия)
An excursion is associated with a guide and a country (Экскурсия -> Гид, Экскурсия -> Страна)
A contract is associated with a tour (Договор -> Туры)
A visited excursion is associated with a contract and an excursion (Посещенные_экскурсии -> Договор, Посещенные_экскурсии -> Экскурсия)
A booking is associated with a client (Бронирование -> Клиенты)
A tourist is associated with a client and a contract (Туристы -> Клиенты, Туристы -> Договор)
A tourist by booking is associated with a booking and a contract (Туристы_по_броне -> Бронирование, Туристы_по_броне -> Договор)

##Usage
Эта база данных может использоваться для управления информацией о турах, клиентах, экскурсиях, отзывах, гидах, контрактах, посещенных экскурсиях, бронированиях, туристах и самих туристах при бронировании в туристическом агентстве.
