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

