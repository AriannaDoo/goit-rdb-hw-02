# goit-rdb-hw-02

## Homework 2 / Домашнє завдання 2

### Topic / Тема:
- Relational Databases
- Database Design
- Normalization (1NF, 2NF, 3NF)
- ER Diagram
- MySQL Workbench

---

## Опис роботи / Project Description

У цьому домашньому завданні було виконано проєктування бази даних на основі початкової ненормалізованої таблиці замовлень.

Було проведено нормалізацію даних до:

- **1NF (Перша нормальна форма)**  
- **2NF (Друга нормальна форма)**  
- **3NF (Третя нормальна форма)**

Після цього створено фінальну структуру бази даних та ER-діаграму в MySQL Workbench.

---

## Initial Table / Початкова таблиця

| Order ID | Product and Quantity | Client Address | Order Date | Client |
|---------|----------------------|---------------|-----------|--------|
| 101 | Laptop:3, Mouse:2 | Khreshchatyk 1 | 2023-03-15 | Melnyk |
| 102 | Printer:1 | Baseina 2 | 2023-03-16 | Shevchenko |
| 103 | Mouse:4 | Komputerna 3 | 2023-03-17 | Kovalenko |

---

# 1NF / Перша нормальна форма

Кожне поле містить лише одне значення. Поле `Product and Quantity` було розділено на окремі поля `Product` та `Quantity`.

| Order ID | Product | Quantity | Address | Date | Client |
|---------|---------|----------|---------|------|--------|
| 101 | Laptop | 3 | Khreshchatyk 1 | 2023-03-15 | Melnyk |
| 101 | Mouse | 2 | Khreshchatyk 1 | 2023-03-15 | Melnyk |
| 102 | Printer | 1 | Baseina 2 | 2023-03-16 | Shevchenko |
| 103 | Mouse | 4 | Komputerna 3 | 2023-03-17 | Kovalenko |

---

# 2NF / Друга нормальна форма

Дані розділено на окремі таблиці, щоб інформація про клієнтів і товари не дублювалася в кожному замовленні.

## Clients

| client_id | client_name | address |
|----------|-------------|---------|
| 1 | Melnyk | Khreshchatyk 1 |
| 2 | Shevchenko | Baseina 2 |
| 3 | Kovalenko | Komputerna 3 |

## Products

| product_id | product_name |
|-----------|--------------|
| 1 | Laptop |
| 2 | Mouse |
| 3 | Printer |

## Orders

| order_id | order_date | client_id |
|---------|------------|-----------|
| 101 | 2023-03-15 | 1 |
| 102 | 2023-03-16 | 2 |
| 103 | 2023-03-17 | 3 |

## Order_Items

| order_item_id | order_id | product_id | quantity |
|--------------|----------|------------|----------|
| 1 | 101 | 1 | 3 |
| 2 | 101 | 2 | 2 |
| 3 | 102 | 3 | 1 |
| 4 | 103 | 2 | 4 |

---

# 3NF / Третя нормальна форма

У 3НФ усунено транзитивні залежності.  
Адреса клієнта зберігається тільки в таблиці `clients`, а назва товару тільки в таблиці `products`.

Фінальна структура бази даних:

## clients

| Column | Type | Description |
|--------|------|-------------|
| client_id | INT, PK | Unique client ID |
| client_name | VARCHAR(100) | Client name |
| address | VARCHAR(255) | Client address |

## products

| Column | Type | Description |
|--------|------|-------------|
| product_id | INT, PK | Unique product ID |
| product_name | VARCHAR(100) | Product name |

## orders

| Column | Type | Description |
|--------|------|-------------|
| order_id | INT, PK | Unique order ID |
| order_date | DATE | Order date |
| client_id | INT, FK | Reference to clients |

## order_items

| Column | Type | Description |
|--------|------|-------------|
| order_item_id | INT, PK | Unique order item ID |
| order_id | INT, FK | Reference to orders |
| product_id | INT, FK | Reference to products |
| quantity | INT | Product quantity |
---

# ER Diagram

Created in MySQL Workbench.

---

