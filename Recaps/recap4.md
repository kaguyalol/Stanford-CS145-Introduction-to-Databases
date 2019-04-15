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
  - **Insert value(_non-Null_) of presC#, but no tuple in MovieExec has such value of cert# attribute**
  - **Update value(_non-Null_) of presC#, but no tuple in MovieExec has such value of cert# attribute**
  - Delete tuple in MovieExec, the value(_non-Null_) of cert# also appears in precC# in Studio
  - Update the value(_non-Null_) of cert#, the old value also appears in precC# in Studio
  
    ***First two violations cannot change, the last two can be avoided by changing referenced relation***

4. References Relations Policies
  - Default Policy
    * Reject violation modifications
    
  - Cascade Policy
    * Update or delete value in referenced table, system will _automatically_ update or delete value in referencing table
    
  - Set-Null Policy
    * Delete one in referenced table and system change another to null
  
    ```sql
    CREATE TABLE Studio (
      name CHAR(30) PRIMAEY KEY,
      address VARCHAR(255),
      presC# INT REFERENCES MovieExec(cert#)
        ON DELETE SET NULL  -- delete tuples of MovieExec, set presC# to null
        ON UPDATE SET CASCADE  -- update cert# in MovieExec, change presC# in Studio
    );
    ```

5. Deferred Checking of Constraints
  - Insert new tuple to MovieExec with new cert# before inserting new one to Studio
  - If declaring cert# be a foreign key referencing presC#, then presC# shou be UNIQUE
    - Cannot insert any new tuple to both MovieExec and Studio
      * Group into one transaction
      * DBMS check the transaction after the whole transaction finished
      * DEFERABLE/ NOT DEFERABLE(default)
        - DEFERRABLE INITIALLY DEFERRED(after transaction)
        - DEFERRABLE INITIALLY IMMEDIATE(after every statement)
        ```sql
        CREATE TABLE Studio (
          name CHAR(30) PRIMARY KEY,
          address VARCHAR(255),
          presC# INT UNIQUE
            REFERENCES MovieExec(cert#)
            DEFERRABLE INITIALLY DEFERRED
        );
        ```
    
