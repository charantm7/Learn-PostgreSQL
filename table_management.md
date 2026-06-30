## <ins>**Creating the Table:**</ins>

`create table if not exists users (id uuid primary key, username varchar(30) unique not null, email varchar(50) unique not null, password varchar(50) not null, first_name varchar(40), last_name varchar(40), bio varchar(100), created_at timestamp not null, last_login timestamp );`

## <ins>**Altering the Table:**</ins>

1) Add columns: `alter table users add column age integer;`

2) Drop columns: `alter table users drop column age;`

3) Rename columns: `alter table users rename column first to first_name;`

4) Set / Drop default: `alter table users alter column age set/drop default 1;`

5) Set / Drop Not null: `alter table user alter column age set/drop not null;`

6) Add Check Constraint: `alter table users add constraint users_age_check check (age>=18);`

7) Add Primary key: `alter table users add constraint users_pkey primary key(id);`

8) Add Foreign Key: `alter table hotels add constraint fk_owner foreign key(owner_id) references users(id);`

9) Add unique: `alter table hotels add constraint hotels_slug_key unique(slug);`

10) Drop Constraint: `alter table users drop constraint <your constraint name>;`

## <ins>**Types of Constraint:**</ins>

1) Primary Key

2) Foreign Key

3) Not Null

4) Default

5) Unique

6) Check