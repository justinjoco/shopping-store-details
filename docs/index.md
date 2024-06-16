# Overview
This page documents my retrospective of my Shopping Store full stack project. I embed a video demo that shows the frontend at work, and the statuses of the database in after different CRUD updates.

# System Design
[Draw.io](https://drive.google.com/file/d/1inmYJVW4eI7bh-OSSD19OOobevA2uMLM/view?usp=drive_link)

# Video Demo
<iframe src="https://drive.google.com/file/d/1FhlwfybegzviEDT2KA5yS1lVR6M5gCAu/preview" width="900" height="480" allow="fullscreen"></iframe>

# Discussion
I wanted to create a non-trivial full stack project that incorporated real-time CRUD updates to a relational database, and a React frontend with somewhat complex component state managment (but, not so complex to require something like Redux). Although creating the database models and backend was relatively straightforward, the frontend was easily the most complex part of this project.

The point of this project was for me to learn Flask and integrating this server with a React frontend and a SQL backend. Any other advanced topics like auth is out of the scope of this project.

In terms of implementing this project, I started with setting up the database models, then store backend, then finally the frontend. 

## Database
For this shopping store, I decided to keep things simple by having Item and Order data models, and an associative table ItemOrder that records the amount purchased of each individual item. I used a Postgres database because of the relations between the different data models, and since there is a lot of community support and documentation on Postgres.

## Backend
I used the Flask framework for Python because it's one of the most popular web frameworks, and it has loads of community support. I used SQLAlchemy, so that I don't need to write pure SQL statements, and so that I learn how to use Object Relational Mapping.

I enjoyed using SQLAlchemy because it automatically joined the data models together based on their relationships with each other. 

I liked Flask because it makes writing REST APIs easy to do, as well as parsing the request headers and bodies. I also didn't know Flask since my professional experience with microservice development was with Spring Boot, Golang, and Node. In addition, it's used a lot in various parts of the tech industry.

I also used Flask-SQLAlchemy since writing code easier.

I chose Python because I mainly cared about writing business logic, and since I didn't feel like fighting with the compiler.

I created separate APIs for customer and admin since I wanted to have the customer be able to make purchases in the current items, and the admins to update, delete, and add new items to the store. The admins can also see the orders for all different users.

Note that there was no true auth in this project, as the API endpoints parse through the request headers for `role` and `userId` to determine permissions. I intend to implement auth in a separate project.

## Frontend
I chose React as the frontend library/framework because it's a popular library in industry, I've had experience with it, and it has a lot of additional libraries to make the UI look pretty.

There was plenty of state management to deal with in the frontend since I had to record the the request bodies to be used in the REST API write calls.


