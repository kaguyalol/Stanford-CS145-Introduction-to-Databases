## Recap 5

1. Constraints on Attributes
  - `NOT NULL` Constraints
    ```sql
    presC# INT REFERENCES MovieExec(cert#) NOT NULL
    ```
    * Could not insert tuple into Studio with no value of presC#
    * Could not use set-null policy
  - Attribute-based `CHECK` Constraints
      ```sql
      presC# INT REFERENCES MovieExec(cert#) 
        CHECK (presC# >= 100000)
      ```
    - _errorneous_ Attemp **similar to foreign key**
      ```sql
      presC# INT CHECK
        (presC# IN (SELECT cert# FROM MovieExec))
      ```
      * Reject null value of precC# if there is no null for cert#
      * Delete value in MovieExec is invisible to the `CHECK`, now that constraints on presC# is violated
    
    
2. Constraints on Tuple
   ```sql
   CREATE TABLE MovieStar (
    name CHAR(30) PRIMARY KEY,
    address VARCHAR(255),
    gender CHAR(1),
    birthday DATE,
    CHECK (gender = 'F' OR name NOT LIKE 'Ms.%')
   );
   ```
 
 
3. Modification of Constaints
   - Giving Name to Constraints
    ```sql 
    name CHAR(30) CONSTRAINTS NameIsKey PRIMARY KEY,
    ```
    ```sql
    CONSTRAINTS RightTitle
      CHECK (gender = 'F' OR name NOT LIKE 'Ms.%')
    ```
    ```sql
    gender CHAR(1) CONSTRAINTS NoAngro
      CHECK (gender IN ('F', 'M')),
    ```
  - Altering Constraints on Tables
    * `DROP`
      ```sql
      ALTER TABLE MovieStar DROP CONSTRAINT NameIsKey;
      ```
    
4. 
