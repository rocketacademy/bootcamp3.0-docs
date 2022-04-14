# 3.6: Heroku

## Introduction

Heroku is a platform that uses AWS EC2 and makes it easy to create and deploy apps. With Heroku we won't have to SSH into an instance and install any software. Heroku has functionality that will make it easier to expand the capacity of our app if traffic ever increases.

## Heroku Setup

Sign up for an account [here](https://www.heroku.com/).

![Simplified Heroku Architecture Diagram](../../.gitbook/assets/heroku-arch-simple.png)

## Dynos

The above illustration describes how the Heroku platform works. We'll see when we run Express.js that it does not listen for traffic directly on HTTP port 80. Heroku has a system of what they call "routers" that can direct incoming port 80 traffic to a fleet of app "dynos".

In your Heroku dashboard you can adjust how many app servers/instances/dynos are running on the Heroku platform. Each dyno is connected to a centralized database server \(in our case Postgres\).

See detailed docs on the entire platform architecture [here.](https://devcenter.heroku.com/categories/heroku-architecture)

## Add-ons

Heroku also allows a system of Heroku internal "add-ons" to connect to your fleet of app dynos. These encapsulate common web application patterns for data storage, app monitoring, search engines, etc. Postgres is one add-on we will provision for every app. See a [full list of add-ons here.](https://elements.heroku.com/addons)

