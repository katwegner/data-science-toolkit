## Access your database with DBeaver

You need to download [DBeaver](https://dbeaver.io). This is a free multi-platform database tool for developers, database administrators, analysts and all people who need to work with databases. 

- Open DBeaver and click on the little blue "plugin plus"-icon.
- Select `PostgreSQL`as database.
- Copy information of the provided Credentials to the connection Settings on DBeaver
    - `Host`
    - `Database`
    - `User`== `Username`
    - `Password`
    - `Port` (should be both times the same number already)
- click on `Test Connection ...`
    - if connection is not causing an error --> Finish
    - otherwise check all your copy/pasted information again (maybe you copied some spaces...)

Now you can have a look at your database: Expand the paths until "Schemas" --> "public" --> "Tables".
You see that right now, you have no saved tables. 
But we want to change that!

## SQL Queries

- **Schema**: 

    We are using one database with different schemas so first we have to choose the right one, (use quotes):
    ```SQL
    SET SCHEMA 'schema_name'; 
    ```

---
- **SELECT FROM**

    The basic command is:
    ```SQL
    SELECT the_data FROM table_name
    ```
   
    - select more than 1 columns with:
      ```SQL
      SELECT column_name_1, column_name_2 FROM table_name
      ```
   
    - select all columns
      ```SQL
      SELECT * FROM table_name
      ```
    - select unique values with:
      ```SQL
      SELECT DISTINCT column_name_1 FROM table_name
      ```

---
- **WHERE**
    Sometimes we want to retrieve only a subset of the data. In those cases, we use the WHERE keyword. 

    ```SQL
    SELECT column_name
    FROM table_name
    WHERE condition
    ```

    `Condition` represents how we want the data to be filtered.

    > **Exercise:** 
    > - get all cases for women
    > - get all cases for men between 20 and 50

----
- **Joining tables**
    (inner join is default)

    ```SQL
    SELECT t1.name, t2.something FROM table1 t1
    INNER JOIN table2 t2 ON t1.key1 = t2.key2
    ```

    > **Exercise:** now with nice names!
    > - get all cases for women
    > - get all cases for men between 20 and 50

---
- **ORDER BY**
    
    Sort by one or more columns

    ```SQL
    SELECT column_name
    FROM table_name
    WHERE condition
    ORDER BY column_name ASC
    ```
    
    The options are `ASC` and `DESC`.

    > **Exercise:** 
    > - get all cases for women, order them by age-groups ascending
    > - get all cases for men between 20 and 50, order them by record_date descending

---
- **MATHEMATICAL FUNCTIONS**

    eg. SUM ,AVG, COUNT, MAX, MIN

    > **Exercise:** 
    > - get average number of cases for women
    > - get maximum number of cases for men

---
- **GROUP BY**
    
    same as in Pandas

    ```SQL
    SELECT column_name_1, MAX(column_name_2) 
    FROM table
    GROUP BY column_name_1
    ```

    > **Exercise:** 
    > - get sum of cases per gender per age group

---
- **HAVING**
    
    The WHERE keyword is always used before GROUP BY. 

    HAVING is used to filter based on the result of a function.

    Eg. only include countries with more than 5 customers:

    ```SQL
    SELECT COUNT(column_name_2), column_name_1
    FROM table
    GROUP BY column_name_1
    HAVING COUNT(column_name_2) > 5; 

---

### General order of SQL Commands:

1. SELECT FROM
2. WHERE
3. GROUP BY
4. HAVING
5. ORDER BY

---
## Resources:

https://en.wikipedia.org/wiki/Database

https://www.c-sharpcorner.com/UploadFile/65fc13/types-of-database-management-systems/

https://www.postgresqltutorial.com/postgresql-create-table/

https://theartofpostgresql.com/blog/2019-09-sql-joins/
