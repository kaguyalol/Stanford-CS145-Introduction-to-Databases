## Recap 7

1. Virtual View
  - not physically exist
  - virtual relations
  - `CREATE`
    * one relation
      ```sql
      CREATE VIEW ParamountMovies AS
        SELECT title, year
        FROM Movies
        WHERE studioName = 'Paramount';
      ```
    * two relation
      ```sql
      CREATE VIEW MovieProd AS
        SELECT title, year
        FROM Movies, MovieExec
        WHERE presC# = cert#;
      ```
  - Query(same as table)
  - Rename Attributes
    ```sql
      CREATE VIEW ParamountMovies(movieTitle, prodName) AS
        SELECT title, year
        FROM Movies
        WHERE studioName = 'Paramount';
      ```
  - Remove
    * `DROP VIEW <view name>`
      - only drop view, no effect on table
    * `DROP TABLE` also drop views
