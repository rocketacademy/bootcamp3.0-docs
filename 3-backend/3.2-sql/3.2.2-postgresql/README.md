# 3.4: SQL Applications

![](../../.gitbook/assets/express-2.jpg)

The final form of the high-level architecture of our web application is a PostgreSQL database server that stores data, an Express.js web server, and user facing functionality in the browser.

When we deploy this application in its final form \(on the service Heroku\) the database will be accessed on a different computer. This is for modularity \(multiple apps or servers may want to access this DB\) and security \(we can define different security rules on the DB server than our app server\) reasons.

