# SQL-tasks

**Option 1**

Create a view from top 1000 rows which are ordered by date. 
```
CREATE VIEW db.view AS
    SELECT TOP 1000 *
    FROM db.table_name
    ORDER BY TheDate;
```
Delete the view.
```
DELETE db.view
  DATEDIFF(day,getdate(),TheDate) < -2;
```

**About DATEDIFF**

Syntax:
```
DATEDIFF(interval, date1, date2)
```
Example:
```
SELECT DATEDIFF(day, '2011/08/26', '2011/08/25') AS DateDiff;
```
The answer is -1.


References:  
https://www.brentozar.com/archive/2018/04/how-to-delete-just-some-rows-from-a-really-big-table/  
https://www.w3schools.com/sql/func_sqlserver_datediff.asp  
https://stackoverflow.com/questions/1588722/delete-items-older-than-a-day-sql-server


**Option 2**
