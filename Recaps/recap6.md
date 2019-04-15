## Recap 6

1. Transaction
  - A group of operations that need to be performed together
  
  `Flights(fltNo, fltDate, seatNo, seatStatus)`
  ```sql
  SELECT seatNo
  FROM Flights
  WHERE seatStatus = 'available' AND filtDate = DATE '2018-12-25' AND fltNo = 288;
  ```
