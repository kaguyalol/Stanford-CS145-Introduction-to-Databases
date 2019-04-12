## Recap 2

1. Bags
  - No need to care about duplicates
  - When getting average, bags are used

2. `SELECT`, `FROM`, `WHERE`
  - SQL is case _insensitive_
  ```SQL
  Movies(title, year, length, genre, studioName, producerC#)
  ```
  - All movies from Disney Studio in 1990 
    ```sql
    SELECT * -- use for selecting attributes, _NOT_ ROWS
    FROM Movies
    WHERE year = 1990 AND studioName = 'Disney';
    ```
  - Projection in SQL
    ```sql
    SELECT title, length -- select specific attributes(columns)
    FROM Movies
    WHERE year = 1990 AND studioName = 'Disney';
    ```
  - `AS`
    * With different headers 
      ```sql
      SELECT title AS name, length AS duration
      FROM Movies
      WHERE year = 1990 AND studioName = 'Disney';
      ```
    * Change attributes values
      ```sql
      SELECT title AS name, length*0.01667 AS lengthInHours
      ```
    * Constants in `SELECT`
      ```sql
      SELECT title AS name, length*0.01667 AS length, '.hrs' AS inHours -- '.hrs' in every row
      ```
      titl | length | inHours
      ---|---|---
      Pretty Woman | 1.8| hrs.
      ... | ...| hrs.
      
  - Operations
    * Not equal `<>`, concate `||`
    * `>`, `<`, OR, AND
      ```sql
      SELECT title
      FROM Movies
      WHERE (year > 1970 OR length < 90) AND studioName = 'MGM';
      ```
    * Two string comparision
      * delete padding, 'string' = '  string'
      * lexicographic order
    
    * Pattern match `s LIKE p`
      * s is a string, p is pattern
      * Retrive a movie name 'star something'
        ```sql
        SELECT title
        FROM Movies
        WHERE title LIKE 'Star ____';
        ```
    * NULL
      * `x IS NULL`, `x IS NOT NULL`
      * If x is null, x+3 is null
      * `TRUE`, `FALSE`, `UNKOWN`
        * `UNKOWN` AND `TRUE` -> `UNKNOWN`
      * Find all non-NULL length tuples
        ```sql
        SELECT *
        FROM Movies
        WHERE length <= 120 OR length > 120; -- if there are null values in length, then do not return them
        ```
  - Ordering
    * Ascending default
    * List by length, among the same lengths, alphabetically
      ```sql
      SELECT *
      FROM Movies
      WHERE year = 1990 AND studioName = 'Disney'
      ORDER BY length, title; -- sort happens on all columns, if select producer, also valid
      ```
 
3. Queries involve more than one relations
  
  
