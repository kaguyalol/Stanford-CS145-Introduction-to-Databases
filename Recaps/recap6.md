## Recap 6

1. Transaction
  - A group of operations that need to be performed together, executed atomically
    * relation
      `Flights(fltNo, fltDate, seatNo, seatStatus)`
    * query
      ```sql
      SELECT seatNo
      FROM Flights
      WHERE seatStatus = 'available' AND filtDate = DATE '2018-12-25' AND fltNo = 288;
      ```
    * update
      ```sql
      UPDATE Flights
      SET seatStatus = 'occupied'
      WHERE seatNo = '22A' AND filtDate = DATE '2018-12-25' AND fltNo = 288;
      ```
    * Transaction: group query and update together and happen at the same time
    * Serilizably: When one customer see seats and booked it, then another customer does such transaction, no conflict
  - Atomicity
   * relation
    `Accounts(acctNo, balance)`
    
   * add
   
    ```sql
    UPDATE Accounts
    SET balance = balance + 100
    WHERE acctNo = 123;
    ```
    
   * substract
   
    ```sql
    UPDATE Accounts
    SET balance = balance - 100
    WHERE acctNo = 456;
    ```
   * combine such two updates, atomically
   * either all operations are performed or none are
 - `START TRANSACTION`, `COMMIT`, `ROLLBACK`
 
 - Read-only Transactions
  ```sql
  SET TRANSACTIONS READ ONLY;
  ```
 - Dirty Reads
  * _dirty date_ means data written by a transaction that have not been commited
  * _dirty reads_ means read of dirty data by another transaction
  * _Allow dirty reads on account transaction may lead to negative balance_
  * Allow dirty reads on seat-booking can speed up the processing time
    * when one customer find and reserve a seat, need approval to commit, before commit, dirty data is read, then another customer cannot book the seat
    ```sql
    SET TRANSACTION READ WRITE
      ISOLATION LEVEL READ UNCOMMITED;
    ```
 - Isolation Levels
  * `SET TRANSACTION ISOLATION LEVEL READ COMMITED`
  * `SET TRANSACTION ISOLATION LEVEL SERIALIZABLE` (default)
  * `SET TRANSACTION ISOLATION LEVEL REPEATABLE READ`
    - a tuple is retrived at the first time, then identical tuple will be retrived if repeat the query
  * `ISOLATION LEVEL READ UNCOMMITED`
  
  Isolation Level | Dirty Reads | Nonrepeatable Reads | Phantoms
  ---|---|---|---
  Read Uncommitted | Allowed | Allowed | Allowed
  Read Committed | Not Allowed | Allowed | Allowed
  Repeatable Read | Not Allowed | Not Allowed | Allowed
  Serializable | Not Allowed | Not Allowed | Not Allowed
 
 


    
    
