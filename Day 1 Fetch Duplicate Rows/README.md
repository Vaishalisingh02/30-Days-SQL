# How to Fetch Duplicate Rows in a Table?

When working with large datasets, identifying and handling duplicate rows is a crucial task. In this post, we'll explore two common methods for detecting duplicate rows in a table using SQL queries.




### Detect Duplicate Rows in a Table

`SELECT emp_name
FROM employee
GROUP BY emp_name
HAVING count(emp_name)>1;`

 
> GROUP BY emp_name groups the rows based on the combination of Name.<br>HAVING COUNT (*) > 1 filters groups that occur more than once, identifying duplicates.
 
 
#### Detect Duplicates Using a Subquery:

`SELECT emp_name
FROM
(SELECT emp_name,count(emp_name) as num
FROM employee
GROUP BY emp_name) as num1
Where num>1;`
 
> The subquery SELECT Name, COUNT (Name) AS num FROM employee table
<br>GROUP BY emp_name creates a temporary table with the count of each Name.
<br> The outer query filters rows where num > 1, returning duplicate names.