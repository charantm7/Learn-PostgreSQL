<ins>**Inserting:**</ins>

`insert into users(username, email, password, last_name, bio, first_name, age, updated_at) values ('charantm', 'charantm@gmail.com', 'Charantm@2005', 'T M', 'i am backend developer', 'Charan', 20, now());`

<ins>**Update:**</ins>

`update users set last_login=now() where username='charantm';`

**<ins>Read / Querying Data:</ins>**

1.  Select: use to select the column names or \* for whole data.
    
    - `select * from users;`
2.  Column Aliases: The specified column can be have a nick name
    
    - `select first_name as first, last_name as last from users;`
3.  Order By: The Query returns the data with the specified order
    
    - `select * from users order by desc;`
    - `select distinct on (first_name) first_name, last_name from users order by first_name desc;`
4.  Select Distinct: It removes the duplicate rows from the result set. and returns the one row out of group of duplicates
    

	 - `select distinct email, first_name, last_name from users;`

5.  Distinct On: It applies the distinct on the specific columns

	- `select distinct on (first_name, last_name) first_name as first, last_name as last from users;`

&nbsp;

* * *

## <ins>Filtering Data: (clauses)</ins>

1.  WHERE Operator: To retrieve rows  that satisfy the conditions.

	- `select first_name, last_name from users where username='charantm';`

2.  AND Operator: It return the row when the both condition satisfied.

	- `select * from users where first_name='uday' and last_name='uday';`

3.  OR Operator: returns the row when one of the condition matches with the row data.

	- `select * from users where first_name='uday' or last_name='uday';`

4.  LIMIT: it is also used to limit the number of rows returned.
    
    - `select * from users order by age desc limit 2;`
    - `select * from users order by age desc offset 2 limit 2;`
5.  FETCH: it is used to limit the number of rows returned similar to limit clause
    
    - `select * from users order by created_at fetch first 5 rows only;`
    - `select * from users order by age desc offset 2 fetch next 2 rows only;`
6.  BETWEEN: it is used to the check the values is with in the range.
    
    - `select first_name, last_name from users where age between 19 and 21;`
    - `select username, length(username) u_length, age from users where username ~* '^(C|U|B)' and age between 18 and 20 order by u_length;`
7.  IN: It returns the row when the data of the column is in the list of data. If you want to find a value in a list of values
    

	 -  `select first_name, last_name from users where first_name in ('uday','Charan','Bhumika');`

8.  LIKE: To find a string that matches a specified pattern.

	 - `select first_name, last_name from users where first_name like 'C%';`
    - `select first_name, last_name from users where first_name like any (array['B%','C%','u%']);`
    - `select first_name, last_name from users where first_name ilike 'U%';` -> case Insensitive

9.  IS NULL: it is used to fetch the data which specified column is null and for not null, which the columns data is not blank
    - `select first_name, last_name from users where first_name  is null;`
    - `select first_name from users where first_name is not null;`