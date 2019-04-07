## Recap 1

1. Data Models
  - Relational models
    * Based on table
  - Semistructured data model, e.g. XML
    * Based on hierarchical nested tagged elements

2. Basis of Relational Models
  - a 2D table called a _relation_
  - Attributes: column names
  - Schema: a set of attributes, e.g. `Movies(title, year, length, genre)`
  - Tuples: a row of relation(other than header), a tuple of attribute values, e.g. `(Gone With the Wind, 1939, 231, drama)`
  - Domains: data type, e.g. `Movies(title:string, year:integer, length:integer, genre:string)`

3. Keys of relations
  - A set of attributes form a key, values of those key attributes cannot be the same for two tuples
  - e.g. a key consists of _title_ and _year_, there are three movie called King Kong, then their years have to be different, `Movies(_title_, _year_, length, genre)`
  
    ```sql
    MovieStar(
        _name_: string,
        address: string,
        gender: string
    );
    ```

4. Data Types
  - `CHAR(n)` vs `VARCHAR(n)`
    * `CHAR` implies that short string pad space to fit fixed length, e.g. `CHAR(5)` -> `'foo  '`
    * `VARCHAR` string-length is used
  - `BIT(n)` vs `BIT VARYING(n)`
    * `BIT(n)` denotes string of length n
    * `BIT VARYING(n)` denotes string up to length n
  - `BOOLEAN`(TRUE, FALSE, UNKNOWN)
  - `INT`/`INTEGER` vs `SHORT INT`
  ```sql
  CREATE TABLE MovieStar(
      name    CHAR(30),
      address VARCHAR(255),
      birthday DATE
  );
  ```

5. Modify Relations Schema
  - ADD
    ```sql
    ALTER TABLE MovieStar ADD phone CHAR(26);
    ```
  - DROP
    ```sql
    ALTER TABLE MovieStar DROP birthday;
    ```
  
