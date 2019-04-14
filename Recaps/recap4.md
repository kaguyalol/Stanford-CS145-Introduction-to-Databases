## Recap 4

1. Foriegn Key
  ```sql
  CREATE TABLE Studio (
    name CHAR(30) PRIMARY KEY,
    address VARCHAR(255),
    presC# INT REFERENCES MovieExec(cert#) -- cert# in MovieExec is a key, value of cert# and presC# must be same
  );
  ```
