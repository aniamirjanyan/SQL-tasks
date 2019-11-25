# SQL-tasks

**Option 1**

Create a view from top 1000 (or more) rows which are ordered by date. 
```
CREATE VIEW db.view AS
    SELECT TOP 1000 *
    FROM db.table_name
    ORDER BY TheDate;
```
Delete the view.
```
DELETE db.view
  WHERE DATEDIFF(day,getdate(),TheDate) < -2;
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
If we want to delete most part of the table (80-90%) we can insert the small part to a new table and truncate the large one.
```
INSERT INTO table2
SELECT * FROM table1
WHERE DATEDIFF(day,getdate(),TheDate) < -2;

TRUNCATE TABLE table1;
```

References:   
https://stackoverflow.com/questions/24213299/how-to-delete-large-data-of-table-in-sql-without-log/41348462


**Option 3**  
It is possible to automate the task using SQL Server Agent.



References:   
https://docs.microsoft.com/en-us/sql/ssms/agent/sql-server-agent?redirectedfrom=MSDN&view=sql-server-ver15  
https://docs.microsoft.com/en-us/sql/ssms/agent/create-a-transact-sql-job-step?view=sql-server-ver15  
