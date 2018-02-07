SQL cheatsheet
======
### Basic Data Types

| Type          | ARGS                                | Example  |
| ------------- |:-----------------------------------:|:--------:|
| CHAR(n)       | Fixed Length at most n,rest padded  | '9301  ' |
| VARCHAR(n)    | Variable length at most n           | 'abc-930'|
| INTEGER       | Allow negative                      | -11      |
| DECIMAL(p,s)  | precision(p) and scale              | 12.45    |
| DATE          | without time                        | 2016-10-04 |
| DATETIME      | withtime with seconds               | 2016-10-04 15:12:12 |

Decimal = Numeric

### Basic Command - MySQL
```SQL
  SHOW TABLES -- List all Table defined in DB
  DESC <tableName> -- Describe the struct 
  EXIT, QUIT -- CTRL+D
);
```

### DDL - Data Definition Language
#### Constrains 
UNIQUE, NOT NULL 

#### Creating Table
```SQL
CREATE DATABASE <tableName> (
  <colName> <datatype> [<constrains>,]
  
  PRIMARY KEY ([<colName>,])
  FOREIGN KEY <colName> REFERENCES <otherCol> (<otherTable>)
);
```

#### Altering Table

```SQL
ALTER TABLE <tableName>
  RENAME TO <newTableName>;
| ADD COLUMN <colName> <datatype> [<constrains>,];
| ADD CONSTRAINT [<constrains>,];
| DROP COLUMN <colName>;
```

### DML - Data Manipulation Language
#### Date
STR_TO_DATE(<string>, <format>) - '%m/%d/%Y'
DATE_SUB(<date>, INTERVAL <num> <YEAR|MONTH|WEEK...>)
  
- CURRENT_DATE (just the date)
- CURRENT_TIME (just the time)
- CURRENT_TIMESTAMP (both date and time)

#### Insert
```SQL
INSERT INTO <TableName> ([<ColName1>,])
VALUES ([<Val>,])
```

#### Update
modifies one or more rows
```SQL
UPDATE <TableName>
SET [<colName> = <newValue>,]
[WHERE <expression>]
```

#### Delete
Remove zero or more rows
```SQL
DELETE FROM <TableName>
[WHERE expression]
```
### Select
Five basic rel op can be combined to express complex queries
- Selection (σ)
- Projection (π)
- Union (U)
- Difference (-)
- Cartesian Product (⨉)
- Natural Join (⋈) -- join by same col name 
- Theta Join (⋈θ) -- join with θ conditions need to be satisfied
- Equijoin - Theta join where θ only use equality 
- Semijoin (⋉) - the result will be only the one of the table, other table col is ignored - EXIST or IN
- Antijoin (▹) - no tuple in left which also in right, also in NOT EXIST or NOT IN
- grouping operator (ᵛ - gamma)
- The duplicate-elimination operator (ᵜ - seed)
- The sorting operator ᵬ- TAU

CONCAT() AS <name> -- concat multiple column into one
 
 Aggregate Functions
- COUNT()
- MIN()
- MAX()
- SUM()
- AVG()
  

```SQL
SELECT [DISTINCT] [<ColName>,]
  |[ COUNT|MIN|SUM|AVG](<ColName>)
FROM [<TableName>] -- Cartesian Product
| FROM <TableName> 
  |NATURAL JOIN <Tablename> AS <Alias>
  |INNER JOIN <Tablename> USING (<ColName>) -- Requires columns with the same name in joined tables.
  |INNER JOIN <Tablename> ON (<ColName>) -- need to specifiy the table
  |[ LEFT|RIGHT|FULL|CROSS JOIN <table> ON <join condition> ]

[ WHERE <conditions> ]
| WHERE <ColName> NOT LIKE '%_r' -- CASE INsensitive

[ GROUP BY <ColName>]
[ HAVING [ COUNT|MIN|SUM|AVG](<ColName>) <conditions>] -- for group by conditions

[ ORDER BY <column(s)> ]
```
SELECT 
UNION [ALL]
SELECT

### View
a quick way to save a SQL query
CREATE VIEW <viewName> AS <viewDefinition>;
  
### Index

CREATE INDEX <index name> ON <table name> (<column(s)>);
  
### Transaction - ACID

START TRANSACTION;

query stuff

-- COMMIT;
-- ROLLBACK;


