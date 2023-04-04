# ProGrad-DBMS-Training
Open SSMS &rarr; Connect &rarr; Right Click Database &rarr; Name DB
<br>
## Create Table

```
CREATE TABLE [dbo].[Student_Details](
	[_id] [int] NOT NULL,
	[name] [nchar](50) NOT NULL,
	[department] [nchar](10) NOT NULL,
	[dateOfBirth] [datetime] NOT NULL,
	[email] [nchar](20) NULL
) ON [PRIMARY]

```

## Alter Table
```
ALTER TABLE [dbo].Student_Details ADD PRIMARY KEY (_id);
```
```
ALTER TABLE [dbo].Student_Details ADD Aadhar int NULL;
```

## Delete Table
```
DROP TABLE table_name;
```

## Insert Data
```
INSERT into [dbo].Student_Details VALUES(1, 'Krithika', 'IT', '2002/04/07 12:13:14', 'krithika.23it@licet');
INSERT into [dbo].Student_Details VALUES(2, 'Priya', 'EEE', '2002/06/05 12:13:14', 'priya.23it@licet');
INSERT into [dbo].Student_Details VALUES(3, 'Nithya', 'Mech', '2002/01/02 12:13:14', 'nithya.23it@licet');
INSERT into [dbo].Student_Details VALUES(4, 'Faizal', 'Mech', '2004/04/04 11:13:14', 'faizal.23it@licet');
```

## Delete Data
```
DELETE FROM [dbo].Student_Details WHERE _id=3 AND Name='Faizal'
```

## Update Data
```
UPDATE [dbo].Student_Details SET email = 'nithya.23it@licet' WHERE _id = 3;
```

## Adding Foreign Key
Scenario: Students must be a part of the departments present only in the Department_Table

```
ALTER TABLE [dbo].[Student_Details]
ADD CONSTRAINT [FK_StudentDetails_DepartmentMaster]
FOREIGN KEY ([department])
REFERENCES [dbo].[Department_Master] ([department]);
```
The value has to be unique.

## Group by vs Having vs Order by 
|    | GROUP BY                                                                                                            | HAVING                                                                                                                          | ORDER BY                                                                                                             |
|----|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Use | To group the results of a SELECT statement by one or more columns                                                   | To filter the results of a GROUP BY query by a specified condition                                                               | To sort the results of a SELECT statement by one or more columns                                                    |
|    |                                                                                                                     |                                                                                                                                  |                                                                                                                      |
| Syntax | SELECT column_name(s) FROM table_name GROUP BY column_name(s);                                                       | SELECT column_name(s) FROM table_name GROUP BY column_name(s) HAVING condition;                                                  | SELECT column_name(s) FROM table_name ORDER BY column_name(s) ASC|DESC;                                                |
|    |                                                                                                                     |                                                                                                                                  |                                                                                                                      |
| Example | SELECT COUNT(*) as num_orders, customer_id FROM orders GROUP BY customer_id;                                      | SELECT COUNT(*) as num_orders, customer_id FROM orders GROUP BY customer_id HAVING num_orders > 10;                             | SELECT last_name, first_name, hire_date FROM employees ORDER BY hire_date DESC;                                      |
|    |                                                                                                                     |                                                                                                                                  |                                                                                                                      |
| Note | The GROUP BY clause must be used in conjunction with an aggregate function (e.g. COUNT, SUM, AVG)                     | The HAVING clause is used to filter the results of a GROUP BY query after the aggregation has taken place                      | The ORDER BY clause can be used with any column(s) in the SELECT statement, and can be sorted in ascending or descending order |










