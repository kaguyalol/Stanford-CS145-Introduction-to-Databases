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
    
