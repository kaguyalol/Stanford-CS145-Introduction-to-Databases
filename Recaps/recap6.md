## Recap 6

1. Transaction
  - A group of operations that need to be performed together
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
    
