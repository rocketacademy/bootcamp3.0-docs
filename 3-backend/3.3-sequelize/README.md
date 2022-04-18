# 3.3: Sequelize

## Introduction

Lets do some wishful thinking...

- _What if we could write a program that writes these SQL queries for us?_
- _What if we did not need to remember this crazy error prone SQL syntax?_
- _What if we could call data their actual names, i.e; `Users`, `Sightings`, rather than the generic `rows`?_

### Introducing Sequelize (our ORM of choice)

[ORM](https://en.wikipedia.org/wiki/Object%E2%80%93relational_mapping) stands for "object-relational mapping", where database tables (also known as "[relations](<https://en.wikipedia.org/wiki/Relation_(database)>)") are mapped to [objects or classes](<https://en.wikipedia.org/wiki/Object_(computer_science)#:~:text=An%20object%20is%20an%20abstract,found%20in%20the%20real%20world.>), such that SQL relations and their relevant associations can be manipulated directly from application code by generating templatized SQL query code. [Sequelize](https://sequelize.org) is the most popular ORM for Node.js. We will use Sequelize during Coding Bootcamp for our web applications to replace raw SQL.

### ORMs Replace Simple SQL Queries

You may have noticed that SQL queries for each set of CRUD routes follow a similar pattern. Most CRUD queries follow this same pattern, and can be relatively easily substituted with ORM syntax by templatizing the standard SQL query syntax.

```sql
// Create Query
INSERT INTO <TABLENAME> (<COLUMN_NAMES>) VALUES (<VALUES>);
// Retrieve Query
SELECT * FROM <TABLE_NAME> WHERE id=<ID>;
```

ORM is the answer to the question: "_What if we could write a program that writes these SQL queries for us?_" When we finish implementing Sequelize ORM in our Express app, it will form the Model part of our Model-View-Controller architecture.

### SQL and Sequelize CRUD Side by Side

Imagine a database setup with the following ERD:

![](../../.gitbook/assets/category-item-erd-wide2.png)

#### SELECT with SQL vs. Sequelize

{% tabs %}
{% tab title="SQL" %}

```javascript
// Find all
SELECT * FROM "categories";

// Find all with specific columns
SELECT id, name FROM "categories";

// Find all with where clause
SELECT * FROM "categories" WHERE createdAt = '2021-20-06'

// Find one
SELECT * FROM "categories" WHERE id = 5 LIMIT 1;
```

{% endtab %}

{% tab title="Sequelize" %}

```javascript
// Find all
Category.findAll();

// Find all with specific columns
Category.findAll({
  attributes: ["id", "name"],
});

// Find all with where clause
Category.findAll({
  where: {
    createdAt: "2021-20-06",
  },
});

// Find one
Category.findOne({
  where: {
    id: 5,
  },
});

// Find by PrimaryKey(id)
Category.findByPk(5);
```

{% endtab %}
{% endtabs %}

#### INSERT and UPDATE with SQL vs.Sequelize

{% tabs %}
{% tab title="SQL" %}

```javascript
// Create
INSERT INTO "categories" (id, name, createdAt, updatedAt)
VALUES (1, 'music', NOW(), NOW());

// UPDATE
UPDATE "categories"
SET name = 'films'
WHERE id = 1;
```

{% endtab %}

{% tab title="Sequelize" %}

```javascript
// Create
Category.create({
  id: 1,
  name: "music",
  createdAt: Date.now(),
  updatedAt: Date.now(),
});

// Update
Category.update({ name: "films", updatedAt: Date.now() }, { where: { id: 1 } });

// Create and update instance, no need for specifying where clause in update
// The created instance acts as reference to the entry in the db
const newCategory = Category.create({
  id: 2,
  name: "cooking",
  createdAt: Date.now(),
  updatedAt: Date.now(),
});

newCategory.update({ name: "gardening ", updatedAt: Date.now() });
```

{% endtab %}
{% endtabs %}

#### DELETE with SQL vs. Sequelize

{% tabs %}
{% tab title="SQL" %}

```javascript
// Delete
DELETE FROM "categories" WHERE id = 1;
```

{% endtab %}

{% tab title="Sequelize" %}

```javascript
// Delete
Category.destroy({
  where: {
    id: 1,
  },
});

// Delete instance
const persistenceCategory = Category.findByPk(1);

persistenceCategory.destroy();
```

{% endtab %}
{% endtabs %}

####
