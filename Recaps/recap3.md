## Recap 3

1. Eliminate Duplicates
  ```sql
  SELECT DISTINCT name
  ```

2. `INSERT INTO`
  ```sql
  Studio(name, address, presC#)
  ```
  ```sql
  Movies(title, year, length, genre, studioName, producerC#)
  ```
  ```sql
  INSERT INTO Studio(name)
  SELECT DISTINCT studioName
  FROM Movies
  WHERE studioName NOT IN
  (SELECT name 
  FROM Studio);
  ```

3. `UPDATE`
  ```sql
  UPDATE MovieExec
  SET name = 'Pres.' || name -- || means concate, adding prefix for name
  WHERE cert# IN 
  (SELECT presC#
  FROM Studio);
  ```
