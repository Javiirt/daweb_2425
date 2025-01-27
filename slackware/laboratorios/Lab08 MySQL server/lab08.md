# Lab 8: MySQL (Optional – for Advanced Students)

## Exercise 8.1

### 1. By executing `SELECT User, Host FROM mysql.user;` find out the number of entries in the user table in the MySQL database.

**Command:**  
```sql
SELECT User, Host FROM mysql.user;
```  
**Answer:**  
This command retrieves all entries in the `mysql.user` table. Count the rows returned to find the total number of entries.

### 2. What are the commands to create and delete a table, and to select data from a table? What about inserting data into a table?

**Commands:**  
- **Create a Table:**  
```sql
CREATE TABLE table_name (column1 datatype, column2 datatype, ...);
```  
- **Delete a Table:**  
```sql
DROP TABLE table_name;
```  
- **Select Data from a Table:**  
```sql
SELECT column_name FROM table_name;
```  
- **Insert Data into a Table:**  
```sql
INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);
```

### 3. Create a database called `nselab`. Within this database, create a table called `users`, with three fields: `studentid`, `firstname`, and `lastname`. 

**Steps:**  
1. Create the database:  
```sql
CREATE DATABASE nselab;
```  
2. Switch to the database:  
```sql
USE nselab;
```  
3. Create the `users` table:  
```sql
CREATE TABLE users (
    studentid INT AUTO_INCREMENT PRIMARY KEY,
    firstname VARCHAR(25) NOT NULL,
    lastname VARCHAR(25) NOT NULL
);
```  
4. Insert two records into the table:  
```sql
INSERT INTO users (firstname, lastname) VALUES ('Joe', 'Bloggs'), ('Ashley', 'Smith');
```  
5. Devise a plan to test validation rules by attempting to insert invalid data or duplicate primary keys and observing the behavior.

## Exercise 8.2 (Optional)

### 1. Create a MySQL user called `adminsec` and grant it full privileges to the `nselab` database only.

**Command:**  
```sql
CREATE USER 'adminsec''localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON nselab.* TO 'adminsec''localhost';
FLUSH PRIVILEGES;
```  
This creates the user `adminsec` with full privileges on the `nselab` database and no access to any other database.

### 2. Create a web page using PHP that can display the data in the `users` table in the `nselab` database.

**PHP Code:**  
```php
<?php
$conn = new mysqli('localhost', 'adminsec', 'password', 'nselab');
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
$sql = "SELECT studentid, firstname, lastname FROM users";
$result = $conn->query($sql);
?>
<!DOCTYPE html>
<html>
<head>
    <title>Users Table</title>
</head>
<body>
    <h1>Users Table</h1>
    <table border="1">
        <tr>
            <th>Student ID</th>
            <th>First Name</th>
            <th>Last Name</th>
        </tr>
        <?php if ($result->num_rows > 0): ?>
            <?php while ($row = $result->fetch_assoc()): ?>
                <tr>
                    <td><?php echo $row['studentid']; ?></td>
                    <td><?php echo $row['firstname']; ?></td>
                    <td><?php echo $row['lastname']; ?></td>
                </tr>
            <?php endwhile; ?>
        <?php else: ?>
            <tr>
                <td colspan="3">No data found</td>
            </tr>
        <?php endif; ?>
    </table>
</body>
</html>
<?php $conn->close(); ?>
```  
This code connects to the MySQL database, retrieves data from the `users` table, and displays it in an HTML table.

**Note:** Replace `'password'` with the actual password for the `adminsec` user.

