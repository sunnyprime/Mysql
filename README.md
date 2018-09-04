# Mysql
I will put all the operation of database.


## open mysql in command line:
```mysql -u root -p ```

and enter your password

## Import database from external source in windows

enter to database:

``` source C:\LEARN\Sample sql\test_db\employees.sql ```



---
## Database Basic commands:

### show database

```show databases; ```

### select database from available database

``` use databasename; ```

### showing available tables from selected databases

``` show tables; ```

### select tables 
```select * from tablename ```

### Create database
``` CREATE DATABASE databasename; ```

### Delete database
``` DROP DATABASE databasename; ```

### create Table
```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

example
```
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255) 
);
```
### Delete Table

``` DROP TABLE table_name; ```

### Alter table

``` ALTER TABLE table_name
ADD column_name datatype;
```
