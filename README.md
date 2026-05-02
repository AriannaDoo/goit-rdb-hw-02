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

Кожне поле містить лише одне значення.

| Order ID | Product | Quantity | Address | Date | Client |
|---------|--------|----------|--------|------|--------|
|101|Laptop|3|Khreshchatyk 1|2023-03-15|Melnyk|
|101|Mouse|2|Khreshchatyk 1|2023-03-15|Melnyk|
|102|Printer|1|Baseina 2|2023-03-16|Shevchenko|
|103|Mouse|4|Komputerna 3|2023-03-17|Kovalenko|

---

# 2NF / Друга нормальна форма

Дані розділено на окремі сутності:

- Clients
- Orders
- Products
- Order_Items

---

# 3NF / Третя нормальна форма

Усунено транзитивні залежності:

- адреса зберігається тільки у `clients`
- назва товару тільки у `products`

---

# Final Tables / Фінальна структура БД

- clients
- orders
- products
- order_items

---

# ER Diagram

Created in MySQL Workbench.

---

# Files

- hw2.sql
- README.md
- Screenshots
