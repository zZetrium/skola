# Databáze
- nejčastěji tzv. Entitně-Relační (E-R)
- obsahují data o Entitách (ucelený předmět např. uživatel, kiha, třída, auto, ...)
    - a jejich vztazích = Relacích
- databázové systémy: např. **MariaDB**, *MySQL*, Oracle, MSSQL, **PostgreSQL**, **SQLite**
- Structured Query Language = SQL = Strukturovaný jazyk pro dotazy
    - DDL - Data definition language -> příkazy pro vytváření struktury
    - DML - Data manipulation language -> příkazy pro manipulaci s daty
        - např. SELECT, INSERT, UPDATE, DELETE

## Vyhledávání v databázi
1. **SELECT** \<sloupec,sloupec,...> *nebo* * **FROM** <tabulka>  
    - **WHERE** \<podmínka>
    - **ORDER BY** \<sloupec,sloupec,...> asc|desc
    - **JOIN** <tabulka>
        - **USING**(\<sloupec>)
        - **ON** \<podmínka>




SELECT customers.contactFirstName,customers.contactLastName,employees.firstName,employees.lastName FROM customers 
JOIN employees ON customers.salesRepEmployeeNumber = employees.employeeNumber
JOIN offices ON employees.officeCode = offices.officeCode
ORDER BY offices.country,offices.city


SELECT products.productName, orders.orderDate, orders.status,
	CASE
    	WHEN orders.status = "Cancelled" THEN orderdetails.quantityOrdered
    END AS quantityOrdered
FROM orders
JOIN orderdetails USING(orderNumber)
JOIN products USING(productCode)
ORDER BY orders.orderDate DESC;
