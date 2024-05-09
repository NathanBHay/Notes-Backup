2SQL is a declarative programming language used to manage [[Databases|database]] structures. SQL is a standardised language which differs in syntax across management software. In a broad sense the goal of the language is to achieve 4 main operations. Those are:
- **Data manipulation**, the ability to add data and change it within a database.
- **Data definition**, a method of creating the structures or schema within a database.
- **Transaction control** which is the process of executing data manipulation operations within the context of a transaction. A transaction being a logical unit of work composing multiple statements.
- **Data control** the controlling of data through commands and access permissions.

In general SQL is able to achieve all of these with the additional benefits of expansions upon the language in the form of **procedural SQL.**

# SQL Queries
A query is an operation which gets data from one or tables containing one or more columns with the possibility of a condition. A query uses a few main operations to retrieve its data. The key one being the `SELECT FROM` operation. The select operation selects a set of rows columns from a list of tables. It is done with the syntax:
```SQL
SELECT colName
FROM tableName
```
A wildcard can be used instead of a column name to get all the columns from a given table. An **alias** can be further used to assign a new name to each column. To assign an alias during the selection operation use `colName AS newName`. Additionally during the declaration of the used column names mathematical operations, and logical operations can be applied.

## Joins
Joins are a method of joining together multiple tables. **Natural Join** is another keyword which can be used to join all rows with matching values, eliminating duplicates. To add a natural join after the from call use `NATURAL JOIN table2`, and use it as many times as required. **Join on** uses a common attribute to join across multiple tables. It is done by calling `JOIN table2 ON condition`. Join on doesn't remove duplicates. **Join using** joins based on a column with the same name. This is called with `JOIN table2 USING (col)`.

**Outer joins** are similar to join on, however instead of joining on a condition, it joins on a condition and keeps values that aren't listed in the left or right table. These joins preface a join on operation and either in left's case keeps the unmatched left entries, the right case keeping unmatched right entries, or full which keeps all unmatched entities.

**Cross join** functions as a cartesian product that creates a $x$ and $y$ axis which are populated with values from both tables.

## Ordering
Order can be achieved through the `ORDER BY ... ASC` or `ORDER BY ... DESC` which sorts a column. By default the ascending option is chosen. The ordering can specify multiple columns as to break ties.

## Where
The where clause is a common clause during a query to select based upon a condition list. These conditions follow traditional logical operations such as `AND`, `OR`, and `NOT` as well as comparison statements. These comparison statements even allowing comparisons of dates. Further comparisons that are unique to the SQL standard include:
- **Between** is a unique operation for SQL that specifies a range `BETWEEN val1 AND val2`.
- The **IN** statement is another which checks if a column's value is in another column, called with `col1 IN col2`. In can also call a list created with parenthesis as to check if the value is in.
- **Like** uses expressions to attempt to match a condition, the two common string matches are `%` which matches base upon any preceding or following characters, and `_` which accepts any character in that place.
- **Is null** checks if a value is null.
- **Upper** is an operation unique to Oracle and switches a value to uppercase which allows for easier string matching. Some applications such as MS will automatically ignore casing.

# Table Creation
Database tables can be created with the operation `create table`, which creates a table based upon the column name, the datatype, and any constraints. This follows the structure:
```SQL
CREATE TABLE tablename(
	col1 datatype contraints,
	col2 datatype contraints,
	PRIMARY KEY (col1),
	FOREIGN KEY (col2) REFERENCES table contraints
);
```
During a create table operation many constraints can be put in place with a space separation. As seen above the `PRIMARY KEY (...)` operation can be used during the creation and after the creation during a modification operation. This operation establishes a value as a primary key which can be used to index the table. The `FOREIGN KEY (...) REFERENCES table` operation is another operation which designates a foreign key located from another table. `DEFAULT` is an operation which assigns a default value to a column if none is given.

Tables can be created from another syntax which relies upon referencing other tables. This syntax is `SELECT` syntax, which attempts to get columns from outside sources. This is done with the syntax:
```SQL
CREATE TABLE tablename AS
SELECT col1, col2, ..., coln
FROM table;
```
This allows the selection of columns from different tables.

# Alter Tables
Tables that have been created can be altered with the `ALTER TABLE` command. This allows edits for data inside a table. Alter operations can either add or modify data.
```SQL
ALTER TABLE table_name
	ADD (colName datatype)
	MODIFY (colName datatype)
	ADD constraint
	ADD PRIMARY KEY (...)
	DROP ...
```
The alter table operation can also be used add constraints with a name, or drop data. During an add operation a primary or foreign key can be specified to change data.

# Indexes
An index is a value that can be used to quickly search for data within the database. Indexes are usually used for data that is searched for commonly as it increases the space of data bases. Indexes can be created with the syntax:
```SQL
CREATE INDEX index_name
ON table_name (col1, col2, ..., coln);
```
The index is commonly specified with the `UNIQUE INDEX` modifier to ensure to duplicate values are allowed. Indexes can also be dropped through the `DROP INDEX` command.

# Constraints
Constraints are operations which restrict the data that can be used to fill a column. Common constraints seen in tables include:
- `NOT NULL` which specifies that a value is mandatory. This is the most common attribute.
- `UNIQUE` creates a unique index on the respective attribute. It is used to remove duplicate values from a column. Occasionally the unique operation isn't stated as some databases assume primary keys to be unique and not null.
- `CHECK (...)` allows for a custom constraint to be specified. The phrase in the brackets is used to check a Boolean condition that given a false result throws an error.

Creation of custom constraints can be done through the use of the `CONSTRAINT ... CHECK` operation. The constraint operation specifies and new constraint and can be placed within a created table, or during an `ADD` operation.

# Data Manipulation
Data can be added to a table, updated and deleted.

## Insertion
To insert data into a table the operation `INSERT` can be used. It is done through:
```SQL
INSERT INTO tableName 
	VALUES(...);
```
This inserts a row into the table, with each successive values operation adding an extra column. `NULL` attributes can be inserted given the value is optional. When adding values with multiple null values a different command can be used. This follows `INSERT INTO tableName(colName)` and allows specified columns to be inserted. Used together insertion operations and selections can be used to transfer data. An example of this is:
```SQL
INSERT INTO table1(col1, col2, col3)
SELECT col1, col2, col3 
FROM table2;
```

## Updates
**Updates** are a more complex operation as conditions need to be specified. To this end the syntax calls a table, and sets values given a condition. This can be expressed as:
```SQL
UPDATE tableName
SET col1='val', col2='val'
WHERE col3='val'
```
The above operation updates two different columns given a third column equal to a certain value. The most common way to change a single value is to call its key. In cases where no condition is specified all values in the column are changed. Updates can be used to run arithmetic operations on values, with mathematical, conditionals, and more being able to be used to change or set custom conditions.

## Deletion
Deletion is handled similar to updates where a condition is specified to be deleted. In general it is advisable to avoid deleting data within a database. It uses the syntax:
```SQL
DELETE FROM tableName
WHERE conditional
```
The where case is optional however if left unspecified drops all data from the tables.

## Rollback
A common operation which attempts to roll back the previous command. It is commonly used to avoid updates or deletion issues.

# Sequences
A sequence is an auto indexed column that is used usually for unique keys. Sequences usually have a name, are used anywhere a value is expected, are not tied to tables or columns, and usually generate a unique value. Most SQL languages follows the syntax:
```SQL
CREATE SEQUENCE name START WITH n INCREMENT BY n1 
```
The specified sequence has the optional arguments start with which specifies a starting values and increment by which sets an increment amount. This means sequences don't necessarily need to be used for unique values. Optionally a `CACHE` or `NO CACHE` operation may be specified for a certain amount of bits to be pre-allocated ahead of time.

During the insertion of data to add a value indexed correctly `seqName.NEXTVAL` or `seqName.CURRVAL` is used within Oracle. For other languages `NEXT VALUE FOR sequenceName` is used.

Sequences can also be dropped from a table with the command `DROP SEQUENCE seqName`

# Procedural SQL
As SQL lacks support for `IF` statements, and looping operations it is common for unique languages to have additional language constructs. Many languages are based upon Oracle's PL/SQL, which has scripts which are enclosed with the `START ... END/` modifiers. The slash at the end of a function specifies the end of a script. Unless specified with a name the value is considered anonymous. Inside these blocks all database operations can be done. A basic print statement takes the form `DBMS_OUTPUT.PUT_LINE('')`.

Variables can be declared with the statement `DECLARE` with each respective variable using the assignment operator `varName datatype := val`.

Loop operations can be called with the either by using `WHILE cond LOOP ... END LOOP` for while loops, or `FOR i in range LOOP ... END LOOP`, for a for loop.

## Triggers
A trigger is a command that happens upon a insertion, deletion or update of date. It can be used to trigger procedural SQL commands within a code block. It uses the syntax:
```SQL
CREATE triggerName
BEFORE OPERATION col ON tableName
FOR EACH ROW
DECLARE 
...
BEGIN
...
END;
```
Triggers can also be `REPLACED` instead of created, can be triggered `BEFORE` or `AFTER` an operation. The `FOR EACH ROW` helps to trigger on a change on any row.

## Procedures
Procedures can be stored to create non-anonymous functions.
