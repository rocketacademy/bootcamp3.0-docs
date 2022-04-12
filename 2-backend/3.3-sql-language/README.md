# 3.3: SQL Language

## Databases

So far we've seen some different ways of storing data:&#x20;

* Data stored in a plain file, separated by line endings (\n)&#x20;
* Data stored as JSON&#x20;
* Binary data, such as images&#x20;

Here we’ll be introducing databases as a store for our data.&#x20;

A database is a collection of tables. A table is made up of columns, rows, and cells - like an Excel spreadsheet. Each row in a database table has a unique identifier, known as the primary key.

A database where different tables are linked together is called a relational database, and this is what we’ll be using. Relational databases are great for organising complex interlinked sets of data. Imagine a social media app and think about all the links between the users, posts, comments, and likes - this can be done with relational databases

![An Excel spreadsheet modelled as a database table](../../.gitbook/assets/screen-shot-2020-11-14-at-2.10.22-pm.png)

{% hint style="info" %}
Non-relational databases also exist, and are sometimes referred to as NoSQL databases.
{% endhint %}

## SQL

SQL (Structured Query Language) is a programming language used to communicate with relational databases. It is used to store, manage, and retrieve data from a database.

SQL is a declarative programming language, which means the code instructs the program what to do, rather than how to do it. Here is an example of some SQL code :

`​​SELECT name FROM cats;`

We are simply instructing SQL to `SELECT` something `FROM` something. All the logic of _how_ to `SELECT` something is taken care of by the language itself (we’ll explain this code in more detail in the next section).
