
# reading-notes

A track for my observations and questions from the reading assignments throughout the ASAC python course.

---

## Code 401 - Advanced Software Development

- > MySQL notes

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

    ---

  - ORDER BY

        SELECT * FROM table1 ORDER BY col1 

    it will sort the results alphabetically by the components of the column (col1)

        SELECT * FROM table1 ORDER BY col1 ASC

    it will sort the results ascendant 

        SELECT * FROM table1 ORDER BY col1 DESC

    it will sort the results descendant 

    ---
    
  - Arithmetic operations 

        SELECT (myGrades + 10) * 100 FROM table1

    it will apply the operation on all the cells in that table and present it as a new untitled table

        SELECT (myGrades + 10) * 100 AS newGrades FROM table1

    it will apply the operation and present the results as a new column named (newGrades)

        SELECT (myGrades + 10) * 100 AS “new grades” FROM table1

    if we want to add a space in between the words of the new name (alias), we have to put them inside single or double quotes 

    ---

  - The "DISTINCT" statement
  
        SELECT DISTINCT col1 FROM table1

    it hides all the duplicates and will only display one of each unique data without any duplicates  

    ---

  - The "JOIN, ON" statement

        SELECT * FROM table1 JOIN table2 ON table2.col2 = table1.col1

    we use the (JOIN) word to extract the common cells for specific two columns (from two different tables), it is important to place each one

---
