# 3.3: Sequelize

## Learning Objectives

1. ORMs allow us to query SQL databases using application languages such as JavaScript
2. Sequelize is the most popular JavaScript ORM
3. Understand basic Sequelize setup and usage
4. Models tell our apps what data they can access; Migrations tell our databases how to be structured

## Introduction

ORMs (Object-Relational Mappings) allow us to manage and query SQL databases using application languages like JavaScript without having to write SQL. This makes our applications more robust because it reduces human error from typos in SQL queries which are typically written as strings. ORMs are a layer on top of SQL, where ORMs translate application code to SQL before querying SQL DBs.

Sequelize is the most popular JavaScript ORM and we will use Sequelize in our applications during Bootcamp. The following sections follow official Sequelize tutorials. There is no need to remember all implementation details from the tutorials. Feel free to skim them, understand high-level concepts and refer back to the tutorials during implementation.



{% embed url="https://youtu.be/XB-0A5nQS1s" %}
Introduction to Databases&#x20;
{% endembed %}

{% embed url="https://youtu.be/6OBhgbS5J-Q" %}
Table Relationships
{% endembed %}

{% embed url="https://youtu.be/dl33mcglPCI" %}
Sequelize Migrations, Seeders and Models
{% endembed %}

{% embed url="https://youtu.be/7Gcm2LjQBYI" %}
Setting up Sequelize in an Express App
{% endembed %}

{% embed url="https://youtu.be/r8U6YKuIIR4" %}
Sequelize Migrations
{% endembed %}

Please checkout the finished code in this [repository](https://github.com/rocketacademy/m3\_sequelize\_repo/tree/initial\_setup), ensure that you're on the `initial_setup` branch.

## Migrations

{% embed url="https://sequelize.org/docs/v6/other-topics/migrations/" %}
Sequelize official tutorial on Sequelize migrations
{% endembed %}

1. We will use migrations to set up our DB schema, the structure of our database, or the tables and their relationships. All companies use migrations to manage DB schema. Rocket considers migrations a core concept of Sequelize and ORMs in general.
2. Migrations at Rocket will only have "development" and "production" environments for simplicity. Tech teams in industry often have "test" environments for more robust testing between development and production.
3. We will use `model:generate` at Rocket to generate model and migration files ( This is done below)
4. You may also use  a command like this: `npx sequelize migration:generate --name products`
5. Rocket will use `.sequelizerc` to specify Sequelize file and folder paths as per the example in "The `.sequelizerc` file" section
6. We will not use concepts from "Dynamic configuration" onward during Rocket's Bootcamp

{% embed url="https://youtu.be/yCPssb0sxds" %}
Primary Migrations
{% endembed %}

{% embed url="https://youtu.be/zJglYvFliiA" %}
Secondary Migrations
{% endembed %}

{% embed url="https://youtu.be/4Wrx_hn_RbM" %}
Tertiary Migrations
{% endembed %}

Please checkout the finished code in this [repository](https://github.com/rocketacademy/m3\_sequelize\_repo/tree/migrations), ensure that you're on the `migrations` branch.



## Seeders

{% embed url="https://sequelize.org/docs/v6/other-topics/migrations/#creating-the-first-seed" %}
Sequelize official tutorial on Sequelize Seeders
{% endembed %}

1. We use seeder files to setup the initial data that can be used to populate our database. All companies will likely seed dummy data so that developers can collaborate and work with similar data.
2. We will use  `npx sequelize seed:generate --name products` command in order to generate our Seeder file
3. Rocket will use seed files to populate initial data in our applications



{% embed url="https://youtu.be/U4ymjMHCya0" %}
Primary Seeders
{% endembed %}

{% embed url="https://youtu.be/sBYRyUEuULM" %}
Secondary Seeders
{% endembed %}

{% embed url="https://youtu.be/BKNk_bh6fFk" %}
Tertiary Seeders
{% endembed %}

Please checkout the finished code in this [repository](https://github.com/rocketacademy/m3\_sequelize\_repo/tree/seeders), ensure that you're on the `seeders` branch.

## Running Migrations and Seeders

{% embed url="https://youtu.be/ug3ZE7e0Abw" %}
Migration Alteration
{% endembed %}

{% embed url="https://youtu.be/cWwxuWO-bu8" %}
Seeder Alteration
{% endembed %}

{% embed url="https://youtu.be/97n2BR5doxM" %}
Running Migrations and Seeders
{% endembed %}

Please checkout the finished code in this [repository](https://github.com/rocketacademy/m3\_sequelize\_repo/tree/running\_migrations\_seeders), ensure that you're on the `running_migrations_seeders` branch if you want to test out the migrations and seeders on your machine you will need to install the dependencies with the command `npm install` after the installation you need to setup your database connections and `.env` after this you can run the migrations, and seeders.



## Model Basics

{% embed url="https://sequelize.org/docs/v6/core-concepts/model-basics/" %}
Sequelize official tutorial on Sequelize models
{% endembed %}

1. A Model is an abstraction that represents a table within your database,  in Sequelize the Model is a class, the instances of this class represent the data stored.&#x20;
2. We will `Extend the Sequelize` `Model` to define models at Rocket
3. We will use default table name inference for all Sequelize examples at Rocket, which automatically assumes table names are the pluralised form of model names
4. When passing in the second object that contains sequelize, we will pass two more key value pairs :&#x20;
   1. `modelName: '<lowercase-name-of-model'>`
   2. `underscored: true`
5. We will not use `model.sync` to synchronise models with databases because that behaviour is not production-safe. We will instead use [database migrations](https://sequelize.org/docs/v6/core-concepts/model-basics/#synchronization-in-production).

{% hint style="info" %}
**Require vs Import Statements**

You may notice that Sequelize docs use `require` syntax to import modules. This is an older import syntax that Node.js still supports. Rocket recommends using `import` syntax for all code we write, and to update file extensions to `.cjs` (short for CommonJS) instead of `.js` for files that use `require` syntax. To enable `import` syntax for all `.js` files by default, Rocket has included a `"type": "module"` setting in `package.json` in all Rocket starter code.
{% endhint %}

## Model Instances

{% embed url="https://sequelize.org/docs/v6/core-concepts/model-instances/" %}
Sequelize official tutorial on Sequelize model instances
{% endembed %}

1. An instance of the Model class represents a row of data that is stored within the Sequelize database.
2. We will use the `create` method to create model instances at Rocket instead of `build` and `save`.
3. Rocket recommends using the suggested way to log model instances with `.toJSON()`
4. Rocket recommends using `update` to update model instances for precision instead of `set` and `save`

## Model Querying - Basics

{% embed url="https://sequelize.org/docs/v6/core-concepts/model-querying-basics/" %}
Sequelize official tutorial on Sequelize model instances
{% endembed %}

1. Model Querying allows developers to preform CRUD like actions to our database, we can preform actions such as create, read update and delete on the database
2. We will use `Model.create()` to insert rows into our database instead of `Model.build()` and `instance.save()`
3. We will rarely need to use syntax in "Advanced queries with functions (not just columns)" section, if ever
4. We will use `Model.bulkCreate` to seed data in our databases for Rocket exercises
5. Limits and pagination will not be necessary until we have large amounts of data that slows down our apps when retrieved all at once

## Model Querying - Finders

{% embed url="https://sequelize.org/docs/v6/core-concepts/model-querying-finders/" %}
Sequelize official tutorial on Sequelize model finder methods
{% endembed %}

1. If you're not updating, inserting or deleting a value from your stored data, you're probably looking to list out some specific information, or even just all the data in your table, use the Model Query Finders to do this.&#x20;
2. These are some of the most common Sequelize methods we will use in our apps
3. We can use the `Instance.findAll()` method to select data from the database to use within our application
   1. You can pass in an object with a where key this helps refine your searches, check out this [example](https://sequelize.org/docs/v6/core-concepts/model-querying-basics/#the-basics).
   2. [Operators](https://sequelize.org/docs/v6/core-concepts/model-querying-basics/#operators) can also be used for advanced queries.
   3. Order and group your data, checkout this [example](https://sequelize.org/docs/v6/core-concepts/model-querying-basics/#ordering-and-grouping).



{% embed url="https://youtu.be/0eS0f84q_RA" %}
Sequelize Models (1)
{% endembed %}



{% embed url="https://youtu.be/BVZS4HIERH0" %}
Sequelize Models (2)
{% endembed %}

Please checkout the finished code in this [repository](https://github.com/rocketacademy/m3\_sequelize\_repo/tree/models), ensure that you're on the `models` branch.

