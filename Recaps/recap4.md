## Recap 4

1. Foriegn Key
  ```sql
  CREATE TABLE Studio (
    name CHAR(30) PRIMARY KEY,
    address VARCHAR(255),
    presC# INT REFERENCES MovieExec(cert#) -- cert# in MovieExec is a key, value of cert# and presC# must be same
  );
  ```

2. Foreign Key Constraints
  - A value appear in one relation must also appear in the primary-key components of another relation
  - Declaring
    * The referenced attributes in second relation must be PRIMARY KEY or UNIQUE
    * Values of foreign key in the first relation must also appear in the referenced attributes of _some tuple_ in the second relation
      * Foreign key value can be null, then no requirement of appearance of null in second table

3. Run-Time ERROR
  - Insert value of presC#, but no tuple in MovieExec has such value of cert# attribute
  - 

4. References Relations Policies
  - Default Policy
    * Reject violation modifications
    
  - Cascade Policy
    * Update or delete value in one table, system will _automatically_ update or delete value in other table
    
  - Set-Null Policy
    * Delete one and system change another to null
  
  ```sql
  CREATE TABLE Studio (
    name CHAR(30) PRIMAEY KEY,
    address VARCHAR(255),
    presC# INT REFERENCES MovieExec(cert#)
      ON DELETE SET NULL
      ON UPDATE SET CASCADE
  );
  ```

5. Deferred Checking of Constraints
  - Insert new tuple to MovieExec with new cert# before inserting new one to Studio
  - 
    
