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
 
6. Default Value
  ```sql
  ALTER TABLE MovieStar ADD phone CHAR(26) DEFAULT '00000';
  ```

7. Declaring Keys
  - `PRIMARY KEY` or `UNIQUE`
  - Declare on the right side of the attribute when creating a new schema
    * use for one attribute in the key
    ```sql
    CREATE TABLE MovieStar(
      name    CHAR(30) PRIMARY KEY,
      address VARCHAR(255),
      birthday DATE
     );
     ```
  - Declare by adding a statement
    * use for both multiples attributes and one attributes
    ```sql
    CREATE TABLE MovieStar(
      name    CHAR(30),
      address VARCHAR(255),
      birthday DATE,
      PRIMARY KEY(name, birthday)
     );
    ```
 
 8. Relational Algebra
  - Set Operations on Relations
    * Union: R U S
    * Intersect: R  S
    * Difference: R - S (differ to S- R)
    
    _Must have the same set of attributes_
  - Projection
    * Produce a new relation that has only some R's columns
    * Duplicate values will be removed
    * Pi_A1, A2, ... , An(R)
    * Pi_title, year, length(Movies)
    
      title | year | length
      --- | --- | ---
      Star War | 1977 | 124
      Galaxy | 1999 | 104
      Wayne's | 1992 | 95
    
    
  
