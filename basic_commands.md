SQL = structured query language

It is the programming language use to have the commands use to query the database.

It is a relational database which stores the structured data in the db

The data is stored in the columns and names

Commands:

1.  create user charantm with password 'Charantm7';
2.  alter database docconvert owner to postgres;
3.  reassign owned by charantm to postgres;
4.  drop owned by charantm;
5.  alter role if exists charantm;
6.  drop database docconvert;
7.  alter role charantm with password 'new';

Creating the connection:

1.  root connection using postgres shell login

&nbsp;       - sudo -i -u postgres

&nbsp;       - psql

&nbsp;       - direct to the psql = sudo -u postgres psql

&nbsp;       - To root connection to db without passwd = sudo -u postgres psql -d docconvert

2\. connect through specific user

&nbsp;       - psql -U charantm -h localhost -p 5432 -d docconvert

&nbsp;

Creating database:

- \> create database test owner=vorex template=template1 encoding='UTF8' connection limit 1 istemplate=True ;

Creating user:

- create user charantm password "char" connection limit 10 superuser createdb createrole login replication ;

Database loading:

- pg_restore -U postgres -h localhost -p 5432 -d dvdrental ~/Desktop/dvdrental.tar

&nbsp;

&nbsp;
