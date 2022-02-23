
# Reading Notes - Mustafa Alahasanat

A track for my observations and questions from the reading assignments throughout the ASAC python course.

---

## Code 102 - Intro to Software Development

---

## Code 201 - Foundations of Software Development

---

## Code 301 - Intermediate Software Development

---

## Code 401 - Advanced Software Development

- > MySQL notes

    ![finish](./screenshots/finish.png)

  - The "USE" statement
  
        USE database1

    it opens the selected database (schema)

    ---

  - The "SELECT, FROM" statement

        SELECT col1 FROM table1

    it opens a column from a table

        SELECT col1, col2, col3 FROM table1

    it opens specific columns from a table

        SELECT * FROM table1

    it opens all columns from a table

    ![Lesson 1](./screenshots/sql1.png)

    ---

  - The "WHERE" statement

        SELECT * FROM table1 WHERE col1 = 1

    it filters the results for only rows who have the column (col1) has the value (1)

        SELECT * FROM table1 WHERE col1 > 300

    it filters the results for values greater than 300
we can use any comparison sign:

    1. ">"
    2. "<"
    3. ">="
    4. "<="
    5. "="
    6. "!=" or "<>"

            SELECT * FROM table1 WHERE col1 = “apple”

    it is a filter for string data types 

        SELECT * FROM table1 WHERE col1 > “1998-09-24”

    it is a filter for date data types, this one display the cells with a date after 24-9-1998 (this is the default format for representing dates in SQL, it takes 4 digits for the year, 2 digits for the month, and 2 for the day)

    ![Lesson 2](./screenshots/sql2.png)

    ---

  - The "AND, OR, NOT" statements

        SELECT * FROM table1 WHERE col1 = “apple” OR col4 < 20  

    we can combine multiple conditions using: AND, OR, NOT

        SELECT * FROM table1 WHERE (col1 = “apple” OR col4 < 20) AND NOT col3 =0

    we can use brackets to cascade conditions

    ---

  - The "IN" statement

        SELECT * FROM table1 WHERE col2 IN (20, 40, 60)  

    we can use the (IN) word to write multiple (OR) conditions, the previous statement is equivalent to this:

    SELECT * FROM table1 WHERE col2 = 20 OR col2 = 40 OR col2 = 60  

        SELECT * FROM table1 WHERE col2 NOT IN (20, 40, 60)  

    we can use the (NOT) in here to get results outside that condition

    ---

  - The "BETWEEN" statement

        SELECT * FROM table1 WHERE col3 BETWEEN 100 AND 300

    we can use the (BETWEEN) word to write a range filter using the (AND) operator, the previous statement is equivalent to this:
    SELECT * FROM table1 WHERE col3 >= 100 AND col3 <= 300

    ---

  - The "LIKE" statement

        SELECT * FROM table1 WHERE col3 LIKE “b%”

    get all the cells where the value of (col3) starts with the letter ( b ) upper and lower cases

        SELECT * FROM table1 WHERE col3 LIKE “%b%”

    get all the cells who have the letter ( b ) in their string

        SELECT * FROM table1 WHERE col3 LIKE “%b”

    get all the cells who ends with the letter ( b ) in their string

        SELECT * FROM table1 WHERE col3 LIKE “_b”

    cells that have ( b ) as the second character in their string (number of underscores indicates the number of voids we want in our filter)

        SELECT * FROM table1 WHERE col3 LIKE “___b”

    cells that have ( b ) as the forth character in their string (because we have 3 underscores)

        SELECT * FROM table1 WHERE col3 LIKE “m____b”

    cells that have ( m ) as the first character and ( b ) as the sixth one (because we have 4 underscores in between)

    ![Lesson 3](./screenshots/sql3.png)

    ---

  - The "ORDER BY" statement

        SELECT * FROM table1 ORDER BY col1 

    it will sort the results alphabetically by the components of the column (col1)

        SELECT * FROM table1 ORDER BY col1 ASC

    it will sort the results ascendant 

        SELECT * FROM table1 ORDER BY col1 DESC

    it will sort the results descendant

    ---

  - The "LIMIT, OFFSET"

        SELECT * FROM table1 LIMIT 5 

    it will display the first 5 rows from the table

        SELECT * FROM table1 OFFSET 3 

    it will display rows starting from the third one till the end

        SELECT * FROM table1 LIMIT 5 OFFSET 3 

    it will display the first 5 rows from the table starting from the third one (3, 4, 5, 6, 7)

    ![Lesson 4](./screenshots/sql4.png)

    ![Lesson 5](./screenshots/sql5.png)

    ---

  - The "DISTINCT" statement
  
        SELECT DISTINCT col1 FROM table1

    it hides all the duplicates and will only display one of each unique data without any duplicates  

    ---

  - The "JOIN, ON" statement

        SELECT * FROM table1 JOIN table2 ON table2.col2 = table1.col1

    we use the (JOIN) word to extract the common cells for specific two columns (from two different tables), it is important to place each one

    ![Lesson 6](./screenshots/sql6.png)

    ---

  - The "INSERT INTO, VALUES" statement

        INSERT INTO table1 (col1, col2, col3) VALUES (val1, val2, val3)

    this will insert a new row in the table and fill its specified columns with the provided values, all required columns must be filled with a suitable values, also number of values must equal number of columns

        INSERT INTO table2 VALUES (val1, val2, val3)

    when we insert in a joined table (suppose table2 is joined with another), we don’t have to specify the columns

    ![Lesson 13](./screenshots/sql13.png)

    ---

  - The "UPDATE" statement

        UPDATE table1 SET col1=”hello", col4=500 WHERE id=11

    it will update the specified columns with the new values

    ![Lesson 14](./screenshots/sql14.png)

    ---

  - The "DELETE, FROM" statement

        DELETE FROM table1 WHERE col3<200

    it will delete all the rows which have a value for (col3) less than 200

    ![Lesson 15](./screenshots/sql15.png)

    ---

  - The "CREATE" statement

        CREATE TABLE IF NOT EXISTS table1 ( 
        id INTEGER PRIMARY KEY,
        col2 TEXT DEFAULT “now”,
        col3 FLOAT, 
        );

    it will create a table with 3 columns: id (a primary key integer), col2 (a string with a default value “now”), col3 (a float)

    ![Lesson 16](./screenshots/sql16.png)

    ---

  - The "DROP" statement

        DROP TABLE IF EXISTS table1

    it will delete the whole table

    ---

  - The "ALTER" statement

    we use it to modify the schema itself (its tables and their constraints and data types)

    - The "ADD" statement

            ALTER TABLE table1 ADD col7 INTEGER DEFAULT 0

        this will add a new column (col7) to the table with the type (integer) and has a default value of (0)

        ![Lesson 17](./screenshots/sql17.png)

        ---

    - The "DROP" statement

            ALTER TABLE table1 DROP col7

        this will delete the whole column (col7)

        ![Lesson 18](./screenshots/sql18.png)

        ---

    - The "RENAME" statement

            ALTER TABLE table1 RENAME TO table2

        this will rename the whole table to (table2)

        ---

  - Arithmetic operations

        SELECT (myGrades + 10) * 100 FROM table1

    it will apply the operation on all the cells in that table and present it as a new untitled table

        SELECT (myGrades + 10) * 100 AS newGrades FROM table1

    it will apply the operation and present the results as a new column named (newGrades)

        SELECT (myGrades + 10) * 100 AS “new grades” FROM table1

    if we want to add a space in between the words of the new name (alias), we have to put them inside single or double quotes
  
    ---

  - Data types in MySQL

    1. INTEGER: an integer value (positive or negative or zero)

    2. BOOLEAN: they represented as an integer value of just 0 or 1

    3. FLOAT: a float value (positive or negative)

    4. DOUBLE: a float value with more capacity (positive or negative)

    5. CHARACTER(num): short strings with a limit of the max characters capacity (num), (longer values may be truncated)

    6. VARCHAR(num_chars): (variable character) strings with a limit of the max characters capacity (num), (longer values may be truncated)

    7. TEXT: strings with an unlimited characters capacity

    8. DATE: a variable with the date as a string 

    9. DATETIME: a variable with the date and the time as a string

    10. BLOB: binary data

    ---

  - Constraints

    1. PRIMARY KEY : this means that the values in this column are unique, and each value can be used to identify a single row in this table

    2. AUTOINCREMENT : only for integer values, this means that the value is automatically filled in and incremented with each row insertion

    3. UNIQUE : this means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table, it differs from the PRIMARY KEY in that it doesn't have to be a key for a row in the table

    4. NOT NULL : this means that the inserted value cannot be NULL

    5. CHECK (expression) : this allows you to run a more complex expression to test whether the values inserted are valid

    6. FOREIGN KEY : this is a consistency check which ensures that each value in this column corresponds to another value in a column in another table, like if there are two tables, one listing people by ID, and another listing their ages, the FOREIGN KEY can ensure that every row in the ages table corresponds to a valid name in the master people list

---
