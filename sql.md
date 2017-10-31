SQL cheatsheet
======

## Create database
```SQL
-- create the database
CREATE DATABASE customers;

-- init columns 
CREATE TABLE costumers( 
  id INT NOT NULL AUTO_INCREMENT , 
  first_name VARCHAR(255),
  last_name VARCHAR(255),
  email VARCHAR(255)
  address VARCHAR(255),
  age INT;
  PRIMARY KEY(id)
 );
```

## Init data to table
```SQL
INSERT INTO customers( first_name, last_name, email, address ) VALUES 
('John', 'Doe', 'jd@gmail.com', 'California'),
('Joseph', 'Alfredo', 'ja@gmail.com', 'Washington'),
('Nick', Sesio', 'ns@gmail.com', 'Arizona');
```

## Update table member
```SQL
UPDATE customers
SET email = 'new@gmail.com'
WHERE id = 3; -- select specify id
```
## Delete table member 
```SQL
UPDATE customers
SET email = 'new@gmail.com'
WHERE id = 3; -- select specify id
```

## Alter table 
```SQL
-- adding new column,  with no data on the new column
ALTER TABLE customers 
ADD COLUMN newCol VARCHAR(255);

-- MODIFY -- mysql
-- ALTER -- other
--
ALTER TABLE customers
MODIFY COLUMN newCol INT(11);  -- 11 max character

ALTER TABLE customers
DROP COLUMN newCol;
```

## Select data 
``` SQL
-- Select all column
SELECT  * FROM customers

-- only select first and last name column
SELECT first_name, last_name FROM customers 

-- Specify customers (use ID because is unique, primary key)
SELECT * FROM customers WHERE id = 2;

-- Display by order according to lastname 
SELECT * FROM customers  ORDER BY lastName ASC;
SELECT * FROM customers  ORDER BY lastName DESC;

-- Give all address 
SELECT address FROM customers;
-- Only one of each
SELECT DISTINCT address FROM customers;

-- With operator
SELECT * FROM customers WHERE age < 30; 
