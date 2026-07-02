
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