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

## Intro to Database Servers

Database servers run applications that allow programs to manipulate the data inside them. In this module we'll learn how to create, manage, and deploy database servers. Note that this is separate from managing the _data_ inside the database, which is done by the SQL language. How SQL interacts with the database server hard drive depends on the particular SQL implementation.

Part of setting up a database is setting up database schema, i.e. what tables and columns are in the database. Web applications typically do not manipulate database schema in response to user actions; application code depends on database schema, but the schema is not defined by the application.

![The data in the database is stored separately from the application code](<../../.gitbook/assets/spaces\_-MHpn6\_lq7F3sPVKqyNy\_uploads\_git-blob-b91d82b347ba55676fd0db8808960cae14874017\_SQL database.jpeg>)

Unlike with the `data.json` file we used prior to SQL, the data inside our database will _not_ be part of the application repo. Database servers are often on separate machines from web application servers, such that they can be accessed by multiple applications. We will see this when we use Heroku, but for now, we will keep our database server on the same machine as our Express app.

![The PostgreSQL server is typically on a separate machine from the web application that accesses it. ](../../.gitbook/assets/spaces\_-MHpn6\_lq7F3sPVKqyNy\_uploads\_git-blob-cdcc69229a31bfe19ec50389a5880edc8509b390\_Postgres.jpeg)

Managing the database server application, e.g. ports, backups, version upgrades, is typically considered developer operations or DevOps and can be a separate role from application development.

## Intro to PostgreSQL

Postgres implements the SQL language in order to store and retrieve data from a set of files on the hard drive.

Postgres is a server application that uses its own TCP/IP protocol, usually on port 5432 (although this is configurable). Requests are sent to the server that contain the SQL language queries for the server to process. The result of the queries is sent back to the client.

Postgres is a software implementation of a database system. So far we've only dealt with a database at a conceptual level, and using that database though SQL.

However, a database system is the actual implementation of something that runs SQL and keeps the data. Each system implements the SQL language slightly differently, keeps the data on the disk in a slightly different way, and gets the data back out differently.

The database system ensures fundamental database properties like [ACID](https://en.wikipedia.org/wiki/ACID) (atomicity, consistency, isolation, durability). A database system needs to account for circumstances like when two opposing queries happen at the same time, or like when a long running INSERT query fails while executing, due to something like power failure. The system doesn't solve these problems, but it is guaranteed to behave in a consistent manner each time.

A database system also includes functionality like automatic data backup and database indexes for increasing query speed.

## psql setup

psql is the Postgres command-line client to access our databases. To help us learn SQL we will use `psql` to manipulate our databases with SQL commands. In later modules we will use a SQL client that allows us to manipulate our databases using a GUI.

### Mac

Install [postgres.app](https://postgresapp.com). Open the application and follow the setup instructions on the website. Do the optional step to configure `$PATH` to use included command line tools.

{% embed url="https://youtu.be/cEOe6WRAhRE" %}
Installing Postgres Mac
{% endembed %}

### Ubuntu (for Windows users in WSL and EC2 Installation)

Install Postgres

```
sudo apt update
sudo apt upgrade
sudo apt install postgresql
sudo apt install postgresql-client
```

Set the Postgres server to start in the background:

```
sudo service postgresql start
```

Set password-less login by opening pg\_hba.conf and copying the below contents into it.

```
sudo chmod 777 /etc/postgresql/12/main/pg_hba.conf
```

```bash
# "sudo" runs the command as the root user
# "$(which code)" gets the location of the VSCode application locally

sudo "$(which code)" /etc/postgresql/12/main/pg_hba.conf
```

If the above command doesn't work, try running VSCode without `sudo`.

```bash
# Open pg_hba.conf in VSCode

code /etc/postgresql/12/main/pg_hba.conf
```

The above will open a new VSCode window.

`pg_hba.conf` contents to copy: (replace the whole file contents with the lines below)

```
# TYPE  DATABASE        USER            ADDRESS                 METHOD

# IPv4 local connections:
local    all            all                                     trust
host     all            all             127.0.0.1/32            trust
# IPv6 local connections:
host     all            all             ::1/128                 trust
```

Restart Postgres to get the new configs:

```
sudo service postgresql restart
```

Login as the user `postgres` - the default root user for the Postgres database. This system user was created when you installed Postgres.

```
sudo su postgres
```

Create a user and database named after your Ubuntu user. We can retrieve our Ubuntu username via the `whoami` command on the command line.

Use the Postgres `createuser` command to create a new Postgres database user that is named the same as your current user.

```
createuser -s <MY_UNIX_USERNAME>
```

Create a default Postgres database named after your current user. We will use DBs named after our usernames to test SQL syntax. Once we start building applications with SQL, we will name our DBs after our applications.

```
createdb <MY_UNIX_USERNAME>
```

Exit out of the `postgres` user

```
exit
```



To interface with Postgres through your command line follow these commands:

```
sudo service postgresql start
sudo su postgres
psql postgres
```

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
