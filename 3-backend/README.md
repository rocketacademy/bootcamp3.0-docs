# 🤖 3: Backend

## Learning Objectives

1. Backend refers to non-client computers that perform logic, store and serve data
2. Servers are computers without a screen that receive requests from clients and respond with data
3. SQL is the language for querying relational databases; PostgreSQL is a popular dialect
4. Sequelize is an ORM (Object-Relational Mapping) that enables us to write code that generates SQL
5. JWT authentication is the de-facto authentication standard
6. Sockets allow us to transmit data and update UIs in real-time
7. Deploy a backend server to Heroku that can store and serve data for our frontends

## Introduction

![We will now build the backend portion of our app architecture. Source: Rocket Academy](<../.gitbook/assets/3 - Backend.png>)

In Module 3: Backend we will build a backend server that performs logic, stores and serves data to our frontends using the JavaScript server framework Express.js. Our backends will use relational (tabled-based) databases (aka SQL databases, pronounced "sequel") instead of the JSON-like databases we used with Firebase. Most companies use SQL databases for the majority of their use cases because SQL can be more structured has less potential for human error.
