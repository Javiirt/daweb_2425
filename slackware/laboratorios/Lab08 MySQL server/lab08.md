# Lab 8: MySQL (Optional – for Advanced Students)

## Exercise 8.1

### 1. By executing SELECT User, Host FROM mysql.user; find out the number of entries in the user table in the mysql database.

#### Respuesta:

![Ejercicio 1, apartado 1](./capturas/lab08-1-1.png)

### 2. What are the commands to create and delete a table, and to select data from a table? What about inserting data into a table? Hint: use the MySQL manual (http://dev.mysql.com/doc/refman/5.1/en/tutorial.html)

#### Respuesta:

![Ejercicio 1, apartado 2](./capturas/lab08-1-2.png)

### 3. Create a database called nselab. Within this database, create a table called users, with three fields: studentid, firstname and lastname. Make studentid the primary key field. This field cannot be empty for anyrecord and should automatically increase by one each time a new record is added (the first record should have a studentid of 1, the second 2 etc.) The other two fields should be limited to a maximum of 25 characters each. Add two students to this table: Joe Bloggs and Ashley Smith. Devise a plan to test the validation rules (this will involve adding more records) and carry it out. 

#### Respuesta:

![Ejercicio 1, apartado 3](./capturas/lab08-1-3.png)

## Exercise 8.2 (Optional)

### 1. Create a MySQL user called adminsec and grant it full privileges to the nselab database only (and no privileges, including viewing, to any other database). You will need to look up the syntax (don’t try to do this by editing the mysql database directly).

#### Respuesta:

![Ejercicio 2, apartado 1](./capturas/lab08-2-1.png)

### 2. Create a web page using PHP that can display the data in the users table in the nselab database. You should try to show in your logbook that you understand what the code does – this could be achieved by annotating the code with comments. (If you are new to PHP, you will need to do some independent research. You may find the following tutorial helpful: http://www.lynda.com/MySQL-tutorials/PHP-MySQL-Essential-Training/119003-2.html. You will need to follow the instructions here to login: http://web.anglia.ac.uk/it/training/lynda/.)

#### Respuesta:

![Ejercicio 2, apartado 1](./capturas/lab08-2-2.png)

![Ejercicio 2, apartado 2](./capturas/lab08-2-3.png)
