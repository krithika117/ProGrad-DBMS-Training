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

## Math Functions
| Function | Description | Syntax | Example |
| --- | --- | --- | --- |
Abs()       | Returns the absolute (positive) value of a number.   | Abs(value)               | Abs(-5) returns 5
Ceiling()   | Returns the smallest integer greater than or equal to a number. | Ceiling(value) | Ceiling(3.14159) returns 4
Floor()     | Returns the largest integer less than or equal to a number. | Floor(value) | Floor(3.14159) returns 3
Round()     | Rounds a number to a specified number of decimal places. | Round(value, decimals) | Round(3.14159, 2) returns 3.14
Round()     | Rounds a number to the nearest integer. If the number is exactly halfway between two integers, the function rounds to the nearest even integer. | Round(value) | Round(3.5) returns 4
Round()     | Rounds a number to a specified number of decimal places using a specified rounding method. The rounding method can be `ToEven` (default) or `AwayFromZero`. | Round(value, decimals, mode) | Round(3.175, 2, MidpointRounding.ToEven) returns 3.18 |
| `Truncate()` | Truncates a number to an integer by removing its decimal part. | `Truncate(value)` | `Truncate(3.14159)` returns `3` |
| `Pow()` | Returns the result of raising a number to a specified power. | `Pow(base, exponent)` | `Pow(2, 3)` returns `8` |
| `Sqrt()` | Returns the square root of a number. | `Sqrt(value)` | `Sqrt(16)` returns `4` |
| `Log()` | Returns the natural logarithm of a number. | `Log(value)` or `Log(value, base)` | `Log(Math.E)` returns `1`, `Log(100, 10)` returns `2` |
| `Exp()` | Returns the result of raising the mathematical constant e to a specified power. | `Exp(value)` | `Exp(1)` returns `2.71828182845905` |









