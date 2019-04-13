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
  - Products and Joins
    ```sql
    SELECT name
    FROM Movies, MoviesExec -- from two tuples
    WHERE title = 'Star Wars' AND producerC# = cert#; 
    -- producerC# from Movies must have same value as that of cert# from MoviesExec
    ```
  - Disambiguating Atrributes
    ```sql
    SELECT Movies.name, MoviesExec.name
    FROM Movies, MoviesExec
    WHERE Movies.address = MoviesExec.address;
    ```
  - Tuple Variables
    * From the same table, diferent tuples
    ```sql
    SELECT star1.name, star2.name
    FROM MovieStar star1, MovieStar star2
    WHERE star1.address = star2.address AND star1.name < star2.name;
    ```
  - Union, Intersect, Difference
    * Intersect
      ```sql
      -- select name and address of all female stars who also with net worth greater than 10000000
      (SELECT name, address
      FROM MovieStar
      WHERE gender = 'F')
      INTERSECT
      (SELECT name, address
      FROM MovieExec
      WHERE netWorth > 10000000);
      ```
    * Except
      ```sql
      -- select movie stars who are not excecutives
      (SELECT name, address
      FROM MovieStar)
      EXCEPT
      (SELECT name, address
      FROM MovieExec);
      ```
    * Union
      ```sql
      -- union movies in Movies and StarsIn
      (SELECT title, year
      FROM Movies)
      UNION
      (SELECT movieTile AS title, movieYear AS year
      FROM StarsIn);
      ```
 
4. Join Expression
  ```
  StarsIn(movieTitle, movieYear, starName)
  ```
  - Cross Join(Product)
    ```sql
    -- 9 columns and 18 rows
    Movies CROSS JOIN StarsIn;
    ```
  - Theta Join
    ```sql
    -- 9 columns
    Movies JOIN StarsIn ON
            title = movieTitle AND year = movieYear;
    ```
    ```sql
    -- 7 columns
    SELECT title, year, length, genre, studioName, producerC#, starName
    FROM Movies JOIN StarsIn ON
    title = movieTitle AND year = movieYear;
    ```
  - Natural Join
    ```sql
    MovieStar NATURAL JOIN MovieExec;
    ```
  - Outerjoins
    * Natural Full Outer Join
      ```sql
      -- columns are same as natural join, but rows are kind of different, with null values
      MovieStar NATURAL FULL OUTER JOIN MovieExec;
      ```
    * Natural Left Outer join
      ```sql
      -- null value based on left relation(table)
      MovieStar NATURAL LEFT OUTER JOIN MovieExec;
      ```
    * Full Outer Join On(outer theta join)
      ```sql
      -- at least one tuple satisfy the condition, other are same as products, but with null 
      MovieStar FULL OUTER JOIN StarsIn ON
      title = movieTitle AND year = movieYear;
      ```
    
  
