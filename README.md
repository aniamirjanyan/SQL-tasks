# SQL-tasks

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



References:
https://www.brentozar.com/archive/2018/04/how-to-delete-just-some-rows-from-a-really-big-table/
