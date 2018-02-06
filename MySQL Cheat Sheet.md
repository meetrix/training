# MySQL CheatSheet

1. Log into mysql:

	mysql -u [username] -p;(will prompt for password)
  
2. Show all databases:
	SHOW DATABASES;
  
3. Access database:
	mysql -u [username] -p [database](will prompt for password)
  
4. Create new database:
	CREATE DATABASE [database_name];
      An error occurs if database exists, Check if the database is existing
      DROP DATABASE IF EXISTS [database_name];
      CREATE DATABASE [database_name];
      
      CREATE DATABASE IF NOT EXISTS Department;
  
5. Select database:
	USE [database_name];
  
6. Determine what database is in use:
	 SELECT DATABASE();
  
7. Show all tables:
	 SHOW TABLES;
  
8. Show table structure:
	 DESCRIBE [table_name];
  
9. List all indexes on a table:
	show index from [table];
  
10. Create new table with columns:
    CREATE TABLE DEPARTMENT             
  ( DNAME VARCHAR(10) NOT NULL,
    DNUMBER INTEGER NOT NULL,
    MGRSSN CHAR(9),
    MGRSTARTDATE CHAR(9) );

11. Adding a column:
	ALTER TABLE EMPLOYEE ADD JOB VARCHAR(12);
    The new attribute will have NULLs in all the tuples of the relation right after the command is executed; hence, the
    NOT NULL constraint is not allowed for such an attribute

12. Adding a column with an unique, auto-incrementing ID:
	ALTER TABLE [table] ADD COLUMN [column] int NOT NULL AUTO_INCREMENT 	PRIMARY KEY;

13. Inserting a record:
  (Insert a tuple for a new EMPLOYEE for whom we only know the FNAME, LNAME, and SSN attributes)
	INSERT INTO EMPLOYEE (FNAME, LNAME, SSN)
  VALUES ('Richard', 'Marini', '653298653')
  
  (Attribute values should be listed in the same order)
  INSERT INTO EMPLOYEE
  VALUES ('Richard','K','Marini', '653298653','30-DEC-92', '98 Oak Forest, Katy,TX', 'M',37000,'987654321', 4);

14. MySQL function for datetime input:
	NOW()

15. Selecting records:
	SELECT * FROM [table_name];
  
  SELECT <attribute list>
  FROM <table list>
  WHERE <condition>
  
  SELECT BDATE, ADDRESS
  FROM EMPLOYEE
  WHERE FNAME='John' AND MINIT='B’ AND LNAME='Smith'

16. Explain records:
	EXPLAIN SELECT * FROM [table];

17. Selecting parts of records:
	SELECT [column], [another-column] FROM [table];

18. Counting records:
	SELECT COUNT([column]) FROM [table];

19. Counting and selecting grouped records:
	SELECT *, (SELECT COUNT([column]) FROM [table]) AS count FROM [table] GROUP BY 	[column];

20. Selecting specific records:
	SELECT * FROM [table] WHERE [column] = [value]; (Selectors: <, >, !=; combine multiple selectors with AND, OR)

21. Select records containing [value]:
	SELECT * FROM [table] WHERE [column] LIKE '%[value]%';

22. Select records starting with [value]:
	SELECT * FROM [table] WHERE [column] LIKE '[value]%';

23. Select records starting with val and ending with ue:
	SELECT * FROM [table] WHERE [column] LIKE '[val_ue]';

24. Select a range:
	SELECT * FROM [table] WHERE [column] BETWEEN [value1] and [value2];

25. Select with custom order and only limit:
	SELECT * FROM [table] WHERE [column] ORDER BY [column] ASC LIMIT 	[value]; (Order: DESC, ASC)

26. Updating records:
	UPDATE [table] SET [column] = '[updated-value]' WHERE [column] = [value];
  
  UPDATE PROJECT
  SET PLOCATION = ‘Galle', DNUM = 5
  WHERE PNUMBER=10

27. Deleting records:
	DELETE FROM [table] WHERE [column] = [value];

28. Delete all records from a table (without dropping the table itself):
	DELETE FROM [table]; (This also resets the incrementing counter for auto generated columns 	like an id column.)

29. Delete all records without deleting schema in a table:
	truncate table [table];

30. Removing table columns:
	ALTER TABLE [table] DROP COLUMN [column];

31. Deleting tables:
	DROP TABLE [table];

32. Deleting databases:
	DROP DATABASE [database];

33. Custom column output names:
	SELECT [column] AS [custom-column] FROM [table];

34. Export a database dump :
	mysqldump -u [username] -p [database] > db_backup.sql

35. Use --lock-tables=false option for locked tables.

36. Import a database dump:
	mysql -u [username] -p -h localhost [database] < db_backup.sql

37. Logout:	exit;

38. To eliminate duplicate tuples in a query result
  SELECT DISTINCT SALARY
  FROM EMPLOYEE

### Aggregate functions

1. Select but without duplicates:
	SELECT distinct name, email, acception FROM owners WHERE acception = 1 AND date >= 	2015-01-01 00:00:00

2. Calculate total number of records:
	SELECT SUM([column]) FROM [table];

3. Count total number of [column] and group by [category-column]:
	SELECT [category-column], SUM([column]) FROM [table] GROUP BY [category-column];

4. Get largest value in [column]:
	SELECT MAX([column]) FROM [table];

5. Get smallest value:
	SELECT MIN([column]) FROM [table];

6. Get average value:
	SELECT AVG([column]) FROM [table];

7. Get rounded average value and group by [category-column]:
	SELECT [category-column], ROUND(AVG([column]), 2) FROM [table] GROUP BY 	[category-column];
  

### Users functions

1. List all users:
	SELECT User,Host FROM mysql.user;

2. Create new user:
	CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';

3. Grant ALL access to user for * tables:
	GRANT ALL ON database.* TO 'user'@'localhost';
	

### MySQL Mathematical Functions

1. Count rows per group	COUNT(column | *)

2. Average value of group	AVG(column)

3. Minumum value of group	MIN(column)

4. Maximum value of group	MAX(column)

5. Sum values in a group	SUM(column)

6. Absolute value	abs(number)

7. Rounding numbers	round(number)

8. Largest integer not greater	floor(number)

9. Smallest integer not smaller	ceiling(number)

10. Square root	sqrt(number)

11. nth power	pow(base,exponent)

12. random number n, 0<n < 1	rand()

13. sin (similar cos, etc.)	sin(number)


### MySQL String Functions

1. Compare strings	strcmp(string1,string2)

2. Convert to lower case	lower(string)

3. Convert to upper case	upper(string)

4. Left-trim whitespace (similar right)	ltrim(string)

5. Substring of string	substring(string,index1,index2)

6. Encrypt password	password(string)

7. Encode string	encode(string,key)

8. Decode string	decode(string,key)

9. Get date	curdate()

10. Get time	curtime()

11. Extract day name from date string	dayname(string)

12. Extract day number from date string	dayofweek(string)

13.Extract month from date string	monthname(string)


### OTHER ACTIONS
###### reset root password

sudo /etc/init.d/mysql stop
sudo mysqld_safe --skip-grant-tables &
mysql -u root
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit

sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start
