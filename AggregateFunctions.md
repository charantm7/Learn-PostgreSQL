Five most important aggregate functions are:

1.  count(): it returns the number of rows in the set
    
2.  sum(): it returns the sum of numerical columns
    
3.  avg(): it returns the avg value of the numerical column
    
4.  min(): it returns the smallest value in the column
    
5.  max(): it returns the maximum value in the column
    

&nbsp;

example:

`select count(*) as total_users, min(age) as minimum_age, max(age) as max_age, avg(age) as average_age, sum(age) as sum_of_age from users;`

1.  Using Group By clause

`select max(age) as oldest, username from users group by username order by oldest desc;`

2\. count the number of users whose age is greater than 20, print the age, first_name, last_name:

`select count(first_name),first_name, last_name , age from users where age>=20 group by last_name, age, first_name;`

&nbsp;

## <ins>**GROUP BY:**</ins>

The group by is used to group the set of rows which has same values so we can apply the aggregate functions on each group like `count()`, `sum()`, `avg()`, `min()`, `max()`

*GROUP BY column → Create groups of same values*

*Aggregate function → Perform calculation on each group*

<ins>example:</ins>

`SELECT department, COUNT(*) FROM employees GROUP BY department;`

&nbsp;

<ins>HAVING CLAUSE:</ins>

The having clause is introduced because where clause cannot used with aggregate functions, so to put conditions for the aggregate included query, we use the having clause.

examples: `select count(first_name) as members, first_name from users group by first_name having count(first_name) > 2;`

&nbsp;