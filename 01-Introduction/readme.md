# Introduction to Databases and its Terminology

What are databases? Why do they exist, what's their purpose? Today we will discuss that.

## History, and Why????

Before the digital revolution of the 60s and 70s, data was initially scattered around papers, documents, lots of different places where it would be hard to find because you would have to scour manually or keep it filed properly. Once computers got better CPUs and became more powerful, you could use them to store and retrieve information at a convenient pace.

Initially, data used to be stored in files, such as the one you are reading right now. While useful in certain practices, it is not useful for keeping track of things such as item quantities, unique items, or other such things, since files are easy to modify without any kind of _constraint_.

Overtime, developers have developed a common language for modifying and querying databases, called SQL ("Structured Query Language"). SQL Ensures that your requests are written properly and that they make sense to the poor computer you will be tormenting with your scripts.

## Database Basics

During the 1970s, you have the development of "Relational Database Management Systems" RDBMS. Relational databases have different **tables**, which connect to eachother in **relationships**. Each table has **columns** or **fields** of information that may have different properties, these can be: constraints, data types, keys, etc etc. An individual item inside of a table is called either a **row** or **entry**. Below you have an example of a database, and what you will be learning to navigate throughout the course.

![Database image](./Intro%20Diagram.drawio.png)

_(Editors note, this is an awfully nice diagram, and a bit complex. I tried to dumb it down as much as I can. Do not worry, details will be explored in later courses.)_

The database has multiple tables, they look very similar to excel spreadsheets. The tables are named as follows: _equipment_, _employee_, _role_, _department_.

### Fields (Columns)

Let's delve in deeper into these tables. **Fields** are the individual rows of a table in this case. (pardon the confusing wording, it will make sense later.). For example, if you look at the _equipment_ table, you will see the **"equipment_id"**. Fields can be _keys_, and they always have a _type_ assigned to them, that describes the kind of data they hold.

#### Keys

**Each table needs to have at a minimum one key**. Keys can be of two types, **Foreign Keys** or **Primary Keys**. Let's talk about them individually.

- **Primary Keys** are the keys used to identify a specific item. Think of it like the identity number on your ID/Drivers License/ Passport. The Primary Keys _must be unique_, as they help with identifying relationships between different tables.

- **Foreign Keys** are the keys used to identify relationships between items. _Foreign keys are always the Primary Key of another table._ An example of this is in the _equipment_ table, the **"employee_id"** column. The employee_id column of the equipment table is the Foreign Key of the equipment table, and the primary key of the employee table. This key marks the relationship between the two tables, if there is an employee_id set to a specific employee, then it means that the employee has borrowed the equipment.

#### Type

Each column has a different type assigned to it. Types describe the kind of data that is contained per column. There are _a lot_ of data types available in database engines, but here are the most commmon data types available:

| Data Type          | Simple Description                             | Example                                  |
| ------------------ | ---------------------------------------------- | ---------------------------------------- |
| `SMALLINT`         | Small whole number.                            | `123`                                    |
| `INTEGER` / `INT`  | Standard whole number.                         | `1000`                                   |
| `BIGINT`           | Large whole number.                            | `9000000000`                             |
| `DECIMAL(p,s)`     | Exact decimal number with fixed precision.     | `19.99`                                  |
| `NUMERIC(p,s)`     | Same as DECIMAL; exact decimal number.         | `123.45`                                 |
| `REAL`             | Approximate decimal number (single precision). | `3.14`                                   |
| `DOUBLE PRECISION` | Approximate decimal number (double precision). | `3.1415926535`                           |
| `SERIAL`           | Auto-incrementing integer.                     | `1, 2, 3`                                |
| `BIGSERIAL`        | Auto-incrementing large integer.               | `100000`                                 |
| `VARCHAR(n)`       | Text with a maximum length.                    | `'Hello'`                                |
| `CHAR(n)`          | Text with a fixed length.                      | `'ABC'`                                  |
| `TEXT`             | Text of variable or unlimited length.          | `'Hello World'`                          |
| `BOOLEAN` / `BOOL` | True or false value.                           | `TRUE`                                   |
| `DATE`             | Stores a calendar date.                        | `'2026-11-24'`                           |
| `UUID`             | Stores a unique identifier.                    | `'550e8400-e29b-41d4-a716-446655440000'` |

**Notes:**

- `p` = total number of digits; `s` = number of digits after the decimal point.
- `n` = total number of letters

You can check this material at any point during the course, and you can also keep it for further use.

#### NULL Parameter

You may have noticed certain columns have a ? next to them (equipment last borrow date is a good example). That one marks if a certain column can be nullable. If a piece of equipment has not been borrowed, then its last borrow date can be marked as null, meaning it was never borrowed.

Generally, programmers like making people's lives harder, so there might be differences in how people write down these details, but for the purpose of this course, assume all data that does **NOT** have a `?` as **MANDATORY** data.

### Relationships

Relationships are marked by **cardinality** and **optionality**. You need to understand these traits in order to properly manipulate entities of a database.

#### Cardinality

Cardinality, as the name implies, represents the number of entities that have the relationship. There are 3 types of cardinality that any one relationship can have.

- **One to One**

This is a relatively rare type of relationship, but as the name implies, one item per one item.

Example: In a particular hospital, the surgeon department has one head of department.

- **One to Many/Many to One**

This is a relationship where one item can have access to many items.

Example: One employee can borrow many equipments. One equipment can be borrowed only by one employee.

- **Many to Many**

This is a rare relationship, because it is something all programmers should avoid (I pray you will never have to deal with this). Many items can have access to many other items

Example: One employee can be part of many departments. One department has many employees.

The issue with the above example, is that there is no easy way to keep a track of this data. Many to Many relationships are always broken into One to Many relationships, using a joint table.

Example: One employee has many roles. One department has given many roles. One role has one employee. One role has one department.

Cardinality is marked by the following arrows, see if you can follow them on the image.

![Cardinality image](./Cardinality.png)

You can also look at [this site](https://www.geeksforgeeks.org/dbms/cardinality-in-dbms/) for more info

#### Optionality

Relationships can be optional or mandatory. This is not talked about too often, as it is relatively obvious, but in this case, the employee - equipment relationship perfectly demonstrates it. Equipment _may be_ borrowed by an employee, but it doesn't have to be. This is an **optional** relationship

An example of a mandatory relationship is the one between department and role, or employee and role. A role **NEEDS** to have an employee, and a role **NEEDS** to have a department, or else it makes no sense.

## Conclusion

This concludes the chapter. You have learnt what a database is, and why it exists. You have learnt what tables are, the columns that forms entities and what kind of data they store.

In the following chapter, you will learn how to use pgAdmin and PostgreSQL in order to create a mock database, which we will use form now. The following chapter will also discuss what entities/rows are, as it is a more practical chapter.

# Pop Quiz

Leave these as a reply, either in the drive or in a message.

1. Describe the relationship between the employees table and equipment table, in your own words.

2. What is the primary key of the department table?

3. What is the foreign key of the role table? Why is it like that?

4. Restaurants have menu items. Menu items are bought by customers. A customer can be in only one restaurant at a time. Write down the relationships and tables, do not get hung up on details.
