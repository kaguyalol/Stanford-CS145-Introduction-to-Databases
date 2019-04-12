## Recap 2

1. Bags
  - No need to care about duplicates
  - When getting average, bags are used

2. `SELECT`, `FROM`, `WHERE`
  ```SQL
  Movies(title, year, length, genre, studioName, producerC#)
  ```
  - `SELECT`
    * all movies from Disney Studio in 1990
      ```sql
      SELECT *
      FROM Movies
      WHERE year = 1990 AND studioName = 'Disney';
      ```
  
  
1. Indexes in SQL
  - Indexes is binary search tree
  
