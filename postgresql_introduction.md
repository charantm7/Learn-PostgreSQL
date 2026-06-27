- SQL = structured query language
- SQL is programming language which helps us to communicate with the database using commands

&nbsp;

<ins>Process occurs after Executing a SQL command:</ins>

1.  `SELECT * FROM users;`
2.  parser -> checks the SQL command syntax, checks if the column and row exists on the table
3.  planner -> it creates a plan to execute the command in such a way like, what are the fastest way to get the data,
    - Going through every row
    - use index on the column if any created
4.  executor -> It performs the plan which is chosen by planner
5.  buffer memory -> postgres does not constantly read data from the disk, cause disk are slow.
    - it acts as a cache memory
    - if the data is present in BM then no disk access needed
6.  storage manager -> It manages the writes, reads, allocating space, managing indexes and table file etc
7.  Physical storage -> real data is stored in here, all the tables are stored in pages and each page contains there rows(tuples) and columns(attributes)

<ins>WAL (Write Ahead logging)</ins> => before changing or modifying actual pages or data, the operations are first written to the WAL and then it is perfromed

- It is useful when the query is executed but disk are not updated, then it sync with the WAL operations and it maintains reliability.

* * *

&nbsp;

When we try to create a new table, postgrSQL does not create the new database records every time instead it copies the blueprints of the database.

- template1:
    - it is the initial blueprint of the database.
    - It contains the needed files like versions, overall it has the cluster of initial files init.
    - By default temp1 is the blueprint for all the database created
    - It can be modified like creating some predefined extensions or some needed tables
- template0:
    - it is the untouched blueprint, and the base blueprint.
    - it contains original blueprint of the database.
    - It can't be modified, so when ever the base blueprint is needed then using the below command can create the database
    - create database test_db template=template0;

&nbsp;

Basic Commands:

1.  `create user charantm with password 'Charantm7';`
    
2.  `alter database docconvert owner to postgres;`
    
3.  `reassign owned by charantm to postgres;`
    
4.  `drop owned by charantm;`
    
5.  `alter role if exists charantm;`
    
6.  `drop database docconvert;`
    
7.  `alter role charantm with password 'new';`
    

Creating the connection:

1.  <ins>Root connection using postgres shell login:</ins>
    - `sudo -i -u postgres`
    - `psql`
    - `sudo -u postgres psql`
    - `sudo -u postgres psql -d docconvert`

<ins>2\. Connect through specific user:</ins>

- `psql -U charantm -h localhost -p 5432 -d docconvert`

<ins>Creating database:</ins>

- `create database test owner=vorex template=template1 encoding='UTF8' connection limit 1 istemplate=True ;`

<ins>Creating user:</ins>

- `create user charantm password "char" connection limit 10 superuser createdb createrole login replication ;`

<ins>Creating Database BackUp:</ins>

- `pg_dump -U postgres -h localhost -F t -d docconvert -f ~/Desktop/docconvert.tar`

<ins>View Backup file:</ins>

- `pg_restore -l ~/Desktop/docconvert.tar`

<ins>Database restore:</ins>

- `pg_restore -U postgres -h localhost -p 5432 -d docconvert ~/Desktop/docconvert.tar`

<ins>Alter database:</ins>

- `alter database test owner to charantm;`
- `alter database test rename to test1;`
- `alter database test set tablespace fastdisk;`

<ins>Rename Database:</ins>

- `\c postgres`
- `select * from pg_stat_activity where datname='test';`
- `select pg_terminate_backend (pid) from pg_stat_activity where datname='test';`
- `alter database test rename to test1;`

<ins>Switch role on Database:</ins>

- `set role your_rolename;`

<ins>Show Database:</ins>

- \\l or \\l+ => list the database
- \\d or \\d+ => describe the relation
- \\du or \\du+ => list the users
- \\c database_name => connect to other DB

Some Basic DB info commands;

- `select version();`
- `select current_database();`
- `select inet_server_addr(), inet_server_port();`
- `select now();`

&nbsp;