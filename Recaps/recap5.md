## Recap 5

1. Constraints on Attributes
  - Not-Null Constraints
    ```sql
    presC# INT REFERENCES MovieExec(cert#) NOT NULL
    ```
    * Could not insert tuple into Studio with no value of presC#
    * Could not use set-null policy
    
