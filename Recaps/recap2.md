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
      SELECT title AS name, length*0.01667 AS length, '.hrs' AS inHours
      ```
      titl | length | inHours
      ---|---|---
      Pretty Woman | 1.8| hrs.
      
  
  
1. Indexes in SQL
  - Indexes is binary search tree
  
