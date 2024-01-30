# MySQL Language Syntax Reference

## Basics
- `CREATE TABLE` with an `AUTO_INCREMENT PRIMARY KEY` and `INDEX` and fill it
- NOTE: This table is used in many examples below
  - ```sql
      CREATE TEMPORARY TABLE IF NOT EXISTS tmpProducts (
        id       int           NOT NULL AUTO_INCREMENT,
        name     varchar(50)   NOT NULL,
        quantity decimal       NOT NULL,
        price    decimal       NOT NULL,
        PRIMARY KEY (id),
        INDEX idx_tmpProducts_name (name)
      );

      INSERT tmpProducts (name, quantity, price) VALUES ('ABC', 1, 10.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('XYZ', 2, 7.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Dog', 5, 55.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Cat', 10, 30.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Toy', 25, 10.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Cam', 4, 75.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Hat', 12, 12.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Ham', 15, 15.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Pop', 48, 2.0);
      INSERT tmpProducts (name, quantity, price) VALUES ('Fig', 20, 0.5);

      -- SELECT * FROM tmpProducts;

- `CREATE TEMPORARY TABLE`
  - NOTE: Exact same syntax as a permenaent table, except you add the keyword `TEMPORARY`
  - IMPORTANT: Temporary tables have many limitations, including not being able to access them more than once in the same query.
  - [TEMPORARY Table Problems](https://dev.mysql.com/doc/refman/5.7/en/temporary-table-problems.html)
  - ```sql
      CREATE TEMPORARY TABLE IF NOT EXISTS tmpProducts (
        id       int           NOT NULL AUTO_INCREMENT,
        name     varchar(50)   NOT NULL,
        quantity decimal       NOT NULL,
        price    decimal       NOT NULL,
        PRIMARY KEY (id),
        INDEX idx_tmpProducts_name (name)
      );

- `CREATE TABLE` on demand from another `TABLE`
  - ```sql
      CREATE TABLE IF NOT EXISTS tmpProductsTop3 AS
          SELECT id, name, quantity, price
            FROM tmpProducts
           ORDER BY (quantity * price) DESC
           LIMIT 3;

      SELECT * FROM tmpProductsTop3;

- `CREATE TABLE` on demand from another `TABLE` and give it an index on disk
- NOTE: `ENGINE=MyISAM` stores the table to disk, allowing `transactions`
  - ```sql
      CREATE TABLE IF NOT EXISTS tmpProductsTop3 (INDEX(name)) ENGINE=MyISAM AS
          SELECT id, name, quantity, price
            FROM tmpProducts
           ORDER BY (quantity * price) DESC
           LIMIT 3;

      SELECT * FROM tmpProductsTop3;

- `CREATE TABLE` on demand from another `TABLE` and give it an index in memory
- NOTE: `ENGINE=MEMORY` stores the table in RAM, which doesn't support `transactions`
  - ```sql
      CREATE TABLE IF NOT EXISTS tmpProductsTop3 (INDEX(name)) ENGINE=MEMORY AS
          SELECT id, name, quantity, price
            FROM tmpProducts
           ORDER BY (quantity * price) DESC
           LIMIT 3;

      SELECT * FROM tmpProductsTop3;

- `CREATE PROCEDURE`
  - ```sql
      CREATE PROCEDURE proc()
      BEGIN
          SELECT 'result';
      END

- `CTE` (Common Table Expression)
  - ```sql
      WITH cte_top3 AS (
        SELECT id
          FROM tmpProducts
        ORDER BY (quantity * price) DESC
        LIMIT 3
      )
      SELECT p.*
        FROM tmpProducts p
        LEFT JOIN cte_top3 t
          ON p.id = t.id
      WHERE t.id IS NULL
      ORDER BY (p.quantity * p.price) DESC
      LIMIT 5;

- `CONCAT()` to concatenate fields of different data types into a string result
  - ```sql
      SELECT CONCAT('ID: ', id) AS id_text, name
	      FROM tmpProducts;

- `CAST` from `INT` to `CHAR`
- [MySQL CAST()](https://www.w3schools.com/sql/func_mysql_cast.asp)
  - ```sql
      SELECT CAST(id AS CHAR) AS id_text, name
	      FROM tmpProducts;

## TOP
- Get the `TOP` 5
  - ```sql
      SELECT id, name, quantity, price
        FROM tmpProducts
       ORDER BY (quantity * price) DESC
       LIMIT 5;

- Get the `TOP` 3 after the `TOP` 5 using an `OFFSET`
  - ```sql
      SELECT id, name, quantity, price
        FROM tmpProducts
       ORDER BY (quantity * price) DESC
       LIMIT 3
      OFFSET 5;
