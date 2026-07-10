The joins are used to combine the related rows from two or more tables using same columns.

<ins>Record:</ins>

Table: users

```SQL
                  id                  | username  | first_name | last_name 
--------------------------------------+-----------+------------+-----------
 04e891ac-6298-41b5-9589-7bdea2ce540b | charantm1 | Charan     | T M
 4441dd03-61b2-40b5-9a48-78cbd557c798 | boomika   | Bhumika    | S N
 f5c3af37-78e9-4fb5-9d72-a992e14059a8 | uday1     | uday       | uday
 de58bd67-0e10-4472-bacd-a48eca2b18b9 | uday      | uday       | T M
 2c4ccdd9-ba6b-4c5b-afc0-9ec0025c7906 | charantm  | Charan     | T M
```

Table: hotels

```SQL
                  id                  |    name     |               owner_id               |       description       |       address       |         created_at         
--------------------------------------+-------------+--------------------------------------+-------------------------+---------------------+----------------------------
 701ed04c-abcc-4f85-91c3-1ee1b9e92cfc | Bhagini     | 2c4ccdd9-ba6b-4c5b-afc0-9ec0025c7906 | Best south Indian hotel | Banglore, Karnataka | 2026-07-10 22:28:37.023689
 9c49254c-9059-424c-b9cf-5b21fef4f586 | Rameshwaram | 2c4ccdd9-ba6b-4c5b-afc1-9ec0025c7906 | North Indian hotel      | New Delhi           | 2026-07-10 23:43:43.761385

```

&nbsp;

1.  Inner Join: It return the only matched rows from both tables

`select first_name, last_name, name from users inner join hotels on hotels.owner_id = users.id;`

result:

```SQL
 first_name | last_name |  name   
------------+-----------+---------
 Charan     | T M       | Bhagini
```

&nbsp;

2.  Left Join: It return all the record from left table and matched record from the right table

`select first_name, last_name, name, description from users left join hotels on hotels.owner_id = users.id;`

Result:

```SQL
 first_name | last_name |  name   |       description       
------------+-----------+---------+-------------------------
 Charan     | T M       |         | 
 Bhumika    | S N       |         | 
 uday       | uday      |         | 
 uday       | T M       |         | 
 Charan     | T M       | Bhagini | Best south Indian hotel
```

&nbsp;

3: Right Join: it returns all the record from right table and only matched record from the left table

`select first_name, last_name, name, description from users right join hotels on hotels.owner_id = users.id;`

Result:

```SQL
 first_name | last_name |    name     |       description       
------------+-----------+-------------+-------------------------
 Charan     | T M       | Bhagini     | Best south Indian hotel
            |           | Rameshwaram | North Indian hotel
```

&nbsp;

4\. Full join: It returns all records from both table and empty or null will be there if not rows matched

`select first_name, last_name, name, description from users full join hotels on hotels.owner_id = users.id;`

Result:

&nbsp;

```SQL
 first_name | last_name |    name     |       description       
------------+-----------+-------------+-------------------------
 Charan     | T M       |             | 
 Bhumika    | S N       |             | 
 uday       | uday      |             | 
 uday       | T M       |             | 
 Charan     | T M       | Bhagini     | Best south Indian hotel
            |           | Rameshwaram | North Indian hotel
```

&nbsp;

5\. Cross Join: combines every row from first table with every row from the second table

sample:

```SQL
colors   size
------   ----
Black	  S
White	  M
          L
        
```

&nbsp;

`select colors.color, sizes.size from colors cross join sizes;` 

Result:

```SQL
color   size
-------------	
Black	S
Black	M
Black	L
White	S
White	M
White	L
```

2 \* 3 = 6 combinations

6\. Self Join: it has no key word it just joins the table with itself;

record: table employees

```SQL
employee_id  |	name   |  manager_id
----------------------------------
    	1    |	Charan |  NULL
    	2    | 	Arun   |  1
    	3    |	Ravi   |  1
    	4    |	Kiran  |  2
```

`select employee.name as employee_name, manager.name as manager from employees as employee left join employees as manager on manager.manager_id = employee.id;`

&nbsp;

```SQL
employee_name	manager_name
----------------------------
    Charan	NULL
    Arun	Charan
    Ravi	Charan
    Kiran	Arun
```

&nbsp;