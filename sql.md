SQL cheatsheet
======
### Basic Data Types
- CHAR(n)
- VARCHAR(n)
- INTEGER
- DECIMAL(p,s)
- DATE
- DATETIME

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
ALTER TABLE <table name>
  RENAME TO <new table name>
| ADD COLUMN <column definition>
| ADD CONSTRAINT <constraint definition>
| DROP COLUMN <column name>  
```
