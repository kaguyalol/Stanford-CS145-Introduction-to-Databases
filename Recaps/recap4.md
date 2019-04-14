## Recap 4

1. Foriegn Key
  ```sql
  CREATE TABLE Studio (
    name CHAR(30) PRIMARY KEY,
    address VARCHAR(255),
    presC# INT REFERENCES MovieExec(cert#) -- cert# in MovieExec is a key, value of cert# and presC# must be same
  );
  ```

2. References Relations Policies
  - Default Policy
  
    Reject violation modifications
    
  - Cascade Policy
  
    update or delete value in one table, system will _automatically_ update or delete value in other table
    
  - Set-Null Policy
  
    delete one and system change another to null
    
