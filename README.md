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
| `Abs()` | Returns the absolute (positive) value of a number. | `Abs(value)` | `Abs(-5)` returns `5` |
| `Ceiling()` | Returns the smallest integer greater than or equal to a number. | `Ceiling(value)` | `Ceiling(3.14159)` returns `4` |
| `Floor()` | Returns the largest integer less than or equal to a number. | `Floor(value)` | `Floor(3.14159)` returns `3` |
| `Round()` | Rounds a number to a specified number of decimal places. | `Round(value, decimals)` | `Round(3.14159, 2)` returns `3.14` |
| `Round()` | Rounds a number to the nearest integer. If the number is exactly halfway between two integers, the function rounds to the nearest even integer. | `Round(value)` | `Round(3.5)` returns `4` |
| `Round()` | Rounds a number to a specified number of decimal places using a specified rounding method. The rounding method can be `ToEven` (default) or `AwayFromZero`. | `Round(value, decimals, mode)` | `Round(3.175, 2, MidpointRounding.ToEven)` returns `3.18` |
| `Truncate()` | Truncates a number to an integer by removing its decimal part. | `Truncate(value)` | `Truncate(3.14159)` returns `3` |
| `Pow()` | Returns the result of raising a number to a specified power. | `Pow(base, exponent)` | `Pow(2, 3)` returns `8` |
| `Sqrt()` | Returns the square root of a number. | `Sqrt(value)` | `Sqrt(16)` returns `4` |
| `Log()` | Returns the natural logarithm of a number. | `Log(value)` or `Log(value, base)` | `Log(Math.E)` returns `1`, `Log(100, 10)` returns `2` |
| `Exp()` | Returns the result of raising the mathematical constant e to a specified power. | `Exp(value)` | `Exp(1)` returns `2.71828182845905` |

## Date Functions
| Function | Description | Syntax | Example |
| --- | --- | --- | --- |
| `Now()` | Returns the current date and time. | `Now()` | `2023-03-29 14:30:00` |
| `Today()` | Returns the current date. | `Today()` | `2023-03-29` |
| `DateAdd()` | Adds a specified time interval to a date. | `DateAdd(interval, number, date)` | `DateAdd("m", 1, #2023-03-29#)` returns `2023-04-29` |
| `DateDiff()` | Returns the difference between two dates. | `DateDiff(interval, date1, date2)` | `DateDiff("d", #2023-03-29#, #2023-04-29#)` returns `31` |
| `DatePart()` | Returns a specified part of a date. | `DatePart(interval, date)` | `DatePart("m", #2023-03-29#)` returns `3` |
| `Year()` | Returns the year of a date. | `Year(date)` | `Year(#2023-03-29#)` returns `2023` |
| `Month()` | Returns the month of a date. | `Month(date)` | `Month(#2023-03-29#)` returns `3` |
| `Day()` | Returns the day of the month of a date. | `Day(date)` | `Day(#2023-03-29#)` returns `29` |
| `Weekday()` | Returns the weekday of a date as a number (1-7, where 1 is Sunday). | `Weekday(date)` | `Weekday(#2023-03-29#)` returns `2` |
| `WeekdayName()` | Returns the name of the weekday for a specified date. | `WeekdayName(weekday, abbreviate)` | `WeekdayName(2, False)` returns `"Monday"`, `WeekdayName(2, True)` returns `"Mon"` |

## String Functions
| Function | Description | Example |
| --- | --- | --- |
| `LEN()` | Returns the number of characters in a string. | `LEN('Hello world')` returns `11` |
| `CONCAT()` | Concatenates two or more strings. | `CONCAT('Hello', ' ', 'world')` returns `'Hello world'` |
| `SUBSTRING()` | Returns a portion of a string. | `SUBSTRING('Hello world', 7, 5)` returns `'world'` |
| `LOWER()` | Converts a string to lowercase. | `LOWER('Hello World')` returns `'hello world'` |
| `UPPER()` | Converts a string to uppercase. | `UPPER('Hello World')` returns `'HELLO WORLD'` |
| `LTRIM()` | Removes leading spaces from a string. | `LTRIM('   Hello World')` returns `'Hello World'` |
| `RTRIM()` | Removes trailing spaces from a string. | `RTRIM('Hello World   ')` returns `'Hello World'` |
| `TRIM()` | Removes leading and trailing spaces from a string. | `TRIM('   Hello World   ')` returns `'Hello World'` |
| `REPLACE()` | Replaces all occurrences of a specified string with another string. | `REPLACE('Hello world', 'world', 'universe')` returns `'Hello universe'` |
| `CHARINDEX()` | Returns the index of the first occurrence of a substring within a string. | `CHARINDEX('world', 'Hello world')` returns `6` |
| `LEFT()` | Returns the specified number of characters from the beginning of a string. | `LEFT('Hello world', 5)` returns `'Hello'` |
| `RIGHT()` | Returns the specified number of characters from the end of a string. | `RIGHT('Hello world', 5)` returns `'world'` |
| `REPLICATE()` | Repeats a string a specified number of times. | `REPLICATE('Hello', 3)` returns `'HelloHelloHello'` |
| `STUFF()` | Deletes a specified length of characters in a string and then inserts another string at the specified position. | `STUFF('Hello world', 6, 5, 'universe')` returns `'Hello universe'` |

## Joins in SQL Server
| Join type | Syntax | Description |
| --- | --- | --- |
| INNER JOIN | `SELECT * FROM table1 INNER JOIN table2 ON table1.column = table2.column` | Returns all rows from both tables where the join condition is true. |
| LEFT JOIN | `SELECT * FROM table1 LEFT JOIN table2 ON table1.column = table2.column` | Returns all rows from the left table and the matching rows from the right table. If there are no matching rows, NULL values are returned. |
| RIGHT JOIN | `SELECT * FROM table1 RIGHT JOIN table2 ON table1.column = table2.column` | Returns all rows from the right table and the matching rows from the left table. If there are no matching rows, NULL values are returned. |
| FULL OUTER JOIN | `SELECT * FROM table1 FULL OUTER JOIN table2 ON table1.column = table2.column` | Returns all rows from both tables, including NULL values where there is no match. |
| CROSS JOIN | `SELECT * FROM table1 CROSS JOIN table2` | Returns the Cartesian product of both tables, i.e. all possible combinations of rows from both tables. |

### Tables present
| employee_id | employee_name | department_id |
| ----------- | ------------- | -------------- |
| 1           | John          | 1              |
| 2           | Jane          | 2              |
| 3           | Mike          | 1              |
| 4           | Susan         | 2              |
| 5           | Tom           | NULL           |

| department_id | department_name |
| -------------- | ----------------- |
| 1              | Finance           |
| 2              | Sales             |
| 3              | HR                |

#### Inner Join
```
SELECT e.employee_id, e.employee_name, d.department_id, d.department_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
```

| employee_id | employee_name | department_id | department_name |
| --- | --- | --- | --- |
| 1 | John | 1 | Finance |
| 2 | Jane | 2 | Sales |
| 3 | Mike | 1 | Finance |
| 4 | Susan | 2 | Sales |

#### Left Join
```
SELECT e.employee_id, e.employee_name, d.department_id, d.department_name
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id;
```
| employee_id | employee_name | department_id | department_name |
| --- | --- | --- | --- |
| 1 | John | 1 | Finance |
| 2 | Jane | 2 | Sales |
| 3 | Mike | 1 | Finance |
| 4 | Susan | 2 | Sales |
| 5 | Tom | NULL | NULL |

#### Right Join
```
SELECT e.employee_id, e.employee_name, d.department_id, d.department_name
FROM employees e
RIGHT JOIN departments d
ON e.department_id = d.department_id;
```
| employee_id | employee_name | department_id | department_name |
| --- | --- | --- | --- |
| 1 | John | 1 | Finance |
| 2 | Jane | 2 | Sales |
| 3 | Mike | 1 | Finance |
| 4 | Susan | 2 | Sales |
| NULL | NULL | 3 | HR |

#### Full Outer Join
```
SELECT e.employee_id, e.employee_name, d.department_id, d.department_name
FROM employees e
FULL OUTER JOIN departments d
ON e.department_id = d.department_id;
```
| employee_id | employee_name | department_id | department_name |
| --- | --- | --- | --- |
| 1 | John | 1 | Finance |
| 2 | Jane | 2 | Sales |
| 3 | Mike | 1 | Finance |
| 4 | Susan | 2 | Sales |
| 5 | Tom | NULL | NULL |
| NULL | NULL | 3 | HR |

### Cross Join
```
SELECT e.employee_id, e.employee_name, d.department_id, d.department_name
FROM employees e
CROSS JOIN departments d;
```
| employee_id | employee_name | department_id | department_name |
| ----------- | ------------- | -------------- | ----------------- |
| 1           | John          | 1              | Finance           |
| 1           | John          | 2              | Sales             |
| 1           | John          | 3              | HR                |
| 2           | Jane          | 1              | Finance           |
| 2           | Jane          | 2              | Sales             |
| 2           | Jane          | 3              | HR                |
| 3           | Mike          | 1              | Finance           |
| 3           | Mike          | 2              | Sales             |
| 3           | Mike          | 3              | HR                |
| 4           | Susan         | 1              | Finance           |
| 4           | Susan         | 2              | Sales             |
| 4           | Susan         | 3              | HR                |
| 5           | Tom           | 1              | Finance           |
| 5           | Tom           | 2              | Sales             |
| 5           | Tom           | 3              | HR                |

## Stored Procedures
### Create Procedure
```
create procedure fetch_employee_salary as select * from employee where salary>=35000;
```

### Alter Procedure
```
ALTER procedure fetch_employee_salary as select * from employee where salary>=30000;
```

### Accepting input
```
ALTER procedure fetch_employee_salary 
@input_base_location nchar(25), 
@input_salary float
as select * from employee where 
base_location = @input_base_location and salary>=@input_salary;
```

### Executing the procedure
```
exec fetch_employee_salary 'Chennai', 20000
```
