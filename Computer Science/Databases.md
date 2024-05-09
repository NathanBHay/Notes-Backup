A database is an organized collection of structed data. A database can be managed through a software interface called a **database management system** (DBMS). A database managing system allows for data to be managed across multiple devices allowing techniques to decentralize the data, as well as access from remote locations. A database usually deals with the basic structure of:
- **Field** which is a group of characters that is used to define and store data.
- **Record** is a logically connected set of multiple fields
- **File** which is a collection of related records.

The conceptual structure of a database is called a **schema**. These schema can be managed with a **data manipulation language**, or defined with a **data definition language**.

A file system exhibits **Structural Dependence** which is a characteristic where changes to the schema affect data access. The inverse being **independence** what changes don't affect data access. Even changes to datatypes cause issues due to the **data dependence** of databases.

Further issues with databases can be seen in its ability to create **data redundancy** due to people repeating data.

# Database Types
There are many types of databases that have been used historically. These types are:
- **File Systems** which function as one mainframe with all resources.
- **Hierarchical & Network** which has basic navigational access.
- **Relational** a form of database that uses relations to format the data.
- **Object Orientated Relational** where OOP principles were adopted for storing data.
- **XML Hybrid** which support unstructured data as well as relational.
- **NoSQL** which removes the relational component to allow for high performance.

There are a variety of classifications for database types. These include:
- **Single/Multi-user** which depends on how many people can access the database at a time.
- **Desktop** which means it runs on a single personal computer.
- **Work group/enterprise** defines what set of people can access the database.
- **Centralized/Distributed** which defines if the data is kept in one location or not.
- **Cloud** which use [[Cloud Computing|cloud]] techniques to store the data.
- **General-purpose/discipline-specific** which defines what the data is.
- **Operational** which means it runs operations whether transactional, production or analytical.
- **Data warehouse** which is a type of database that stores historical data.
- **Structured/Unstructured** which means the data has been formatted to facilitate a specific need.

# Data Model
Data modeling is the process of modelling data in a representation that allows for the creation of a database. The most basic form within data modelling is the **entity**. An entity is a person, place, thing, or event which data will be stored. An entity has characteristics called **attributes**. Attributes commonly have **constraints** that limit what it is defined as. Attributes usually named after an abbreviation of their entity plus there name. This follows the format of `entity_attributw`. Attributes are equivalent to fields within a database. A **relationship** describes an association among entities. There are multiple types of relationships which define its domain. These are:
- **One-to-many** where one entity can generated multiple entities.
- **One-to-one** where one entity manages a single instance of that entity.

# Relational Database
A relational database operates under the idea of relations that make up their own tables of data. This can be sharing key-value pairs or more. A relational database's entities are called **relational tables**. Each table has a row which represents a single entity occurrence, and a set of columns which represent attributes. Beyond this every table needs a uniquely identifiable attribute. This attribute is called the **key**. A key consists of one or more attributes that determine other attributes.

## Keys
Keys are based on the concept of **determination**. Determination is the state of knowing which value one attributes is to determine others. When this process happens it is called a **functional dependence**.

There are multiple types of keys depending on the relational model. These types are:
- **Composite keys** which are keys combined of multiple keys.
- **Super keys** which is a key that can uniquely identify any row.
- **Candidate key** which is a super key that does not contain a subset of attributes that is a super key itself.
- **Primary keys** which are a candidate key selected to uniquely identify all attribute values in a row.
- **Foreign keys** which are attributes in one table whose values match the primary key in another.
- **Secondary keys** which are used for data retrieval by combining keys.

## Attributes
Attributes can be classified as simple or composite. A **composite** attribute is an attribute that can be further subdivided into other attributes. A **simple** attribute is the lowest level where an attribute can no longer be subdivided. Attributes can also be single or multivalued. With **multivalued** attributes being a list of attributes, rather than a single valued attribute which only contains one piece of data. **Derived** attributes are calculated from other attributes, and are not kept within the database, but rather found with algorithms.

## Relationships
Relationships are described using a **connectivity**, whether it be a one-to-one, or one-to-many. The **cardinality** further expresses the maximum and minimum of these relations. Relationships have a variety of strengths based on how the primary key of a related entity are defined. These relationships can be **weak** or non-identifying if the primary key of the child entity does not contain a primary key component in the parent. **Strong** relationships exist when the primary key of the related entity contains the primary key of the parent.

The **degree** of a relationship indicates the number of entities or participants associated with a relationship. These can be unary, binary, ternary or more. **Recursive** relationships exist between rows of the same entity.

## Entities
An entity in a relational database is can be **existence-dependent** if it can only exist in the database when its associated with another related entity occurrence. Conversely if an entity is **existence-independent** then it exists apart from one or more entities. A **strong entity** is an entities where all relationships are independent.

## Relational Algebra
Relational algebra is a set of theoretical ways to manipulate tables contents using relational operators. Variables are considered relational variables and contain a header and a body. The header contains the names of attributes and the body contains the relation. To change these relational variables relational operators are used. Relational operators have the property of closure. Some common relational operators are:
- **Select** or restrict is a unary operator that yields a horizontal subset of the table,
- **Project** provides all values for a selected attribute.
- **Union** combines all rows from two tables, excluding duplicates.
- **Intersect** only gets the rows that are in both tables.
- **Product** which yields all pairs of rows from two tables.
- **Join** yields rows from two tables based on a criteria.
- **Natural join** which creates a new table with only rows with common values.
- **Join columns** which joins based on columns.
- **Equijoin** which links tables based on equality.
- **Theta join** which couples tables using an inequality.
- **Inner join** which joins only rows given a certain criteria, with **outer join** being the opposite.
- **Divide** which answers queries about one set of data.

# Normalisation
Database normalisation is a process of refining a database model as to avoid errors when inserting, updating, and deleting data. It functions to analyse primary and candidate keys. This process usually happens during the switch from conceptual model to a real model. Normalisation follows a step by step procedure of UNF, 1NF, 2NF, 3NF, and occasionally more.
- **Unnormalized form** is the basic form of a database where it is yet to have any relations, only a single large database which includes all the values.
- **1NF** process is done by identifying the candidate keys, and the full/partial dependency relations. It is considered 1NF if a unique primary key has been identified for every row, and it is a valid relation with no null PK, and a single value for each cell, and finally that all attributes are functionally dependent on all or part of the primary key. This process normally removes bracketed entities.
- **2NF** means that all non-key attributes are functionally dependent on the primary key, and all non-key attributes are functionally dependent on any candidate key.
- **3NF** is if all transitive dependencies have been removed. This is done by removing transitive dependencies into new relations,

[[Database Transactions]]
