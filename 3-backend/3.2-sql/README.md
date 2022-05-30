# 3.2: SQL

## Learning Objectives

1. SQL is a robust, mature and the most popular query language for relational databases
2. Understand basic SQL commands
3. PostgreSQL is a popular SQL dialect and database server application
4. \[Nested submodules] Understand 1-M and M-M SQL relationships and corresponding table structures
5. \[Nested submodules] Understand how to set up a SQL database with a backend API server
6. \[Nested submodules] Understand how to design SQL database schemas for different business applications

## Introduction

SQL (Structured Query Language) is a robust, mature and the most popular query language for relational databases. We use SQL to store, manage, and retrieve data from relational databases, aka SQL databases.

A relational database is a database composed of "relations", also known as tables. Tables are like spreadsheet tables with headers in the first row, each identifying the data that will be in its respective column.&#x20;

A primary strength of relational databases is their ability to represent relationships in data. For example, in a social media app I might have a `users` table and a `posts` table, and a relational database would be able to represent that each post belongs to a user, and that a user has many posts.

## PostgreSQL

PostgreSQL (aka "Postgres") is a popular and robust SQL dialect that is both lightweight and feature-rich. Other popular SQL dialects include MySQL (heavy, feature-rich) and SQLite (light, less feature-rich).

Postgres is also a database server application that we will use to store and retrieve data for our apps using the Postgres language. Postgres is typically run on its own server in production for modularity (multiple apps may want to access this DB) and security (different security rules for our DB vs API server).

## Post-Class Exercises: Codecademy Learn SQL

Complete all exercises in the following Codecademy lessons when they are assigned in the Rocket course schedule.

The following exercises introduce basic SQL syntax. We will not write much SQL during Rocket because we will rely on ORMs (Object-Relational Mappings) such as Sequelize to construct SQL using JavaScript for more robust applications. However, it is relevant to know SQL syntax and some companies test for it during interviews.

1. [Manipulation](https://www.codecademy.com/courses/learn-sql/lessons/manipulation/exercises/sql)
2. [Queries](https://www.codecademy.com/courses/learn-sql/lessons/queries/exercises/queries)
3. [Aggregate Functions](https://www.codecademy.com/courses/learn-sql/lessons/aggregate-functions/exercises/intro)
4. [Multiple Tables](https://www.codecademy.com/courses/learn-sql/lessons/multiple-tables/exercises/intro) (left joins, cross joins, unions and "with" syntax are more niche and less important for Bootcamp, but may be helpful in data analyst work)

## Additional Resources

1. Codecademy SQL cheatsheets for [Manipulation](https://www.codecademy.com/learn/paths/learn-sql/tracks/learn-sql/modules/learn-sql-manipulation/cheatsheet), [Queries](https://www.codecademy.com/learn/paths/learn-sql/tracks/learn-sql/modules/learn-sql-queries/cheatsheet), [Aggregate Functions](https://www.codecademy.com/learn/paths/learn-sql/tracks/learn-sql/modules/learn-sql-aggregate-functions/cheatsheet) and [Multiple Tables](https://www.codecademy.com/learn/paths/learn-sql/tracks/learn-sql/modules/learn-sql-multiple-tables/cheatsheet)
2. [This CS50 video](https://www.youtube.com/watch?v=gu980iXwY5c) explains common SQL syntax
3. [Article on when to choose MySQL vs Postgres](https://developer.okta.com/blog/2019/07/19/mysql-vs-postgres)
4. [ACID properties](https://en.wikipedia.org/wiki/ACID) required of all production databases
