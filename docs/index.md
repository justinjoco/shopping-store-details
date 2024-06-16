# Overview
This page documents my retrospective of my Shopping Store full stack project. I embed a video demo that shows the frontend at work, and the statuses of the database in after different CRUD updates. [Project link](https://github.com/justinjoco/shopping-store)

# System Design
The following Draw.io link shows my requirements for this project, the data models, and the REST APIs exposed by the backend.
[Draw.io](https://drive.google.com/file/d/1inmYJVW4eI7bh-OSSD19OOobevA2uMLM/view?usp=drive_link)

# Video Demo
<iframe src="https://drive.google.com/file/d/1FhlwfybegzviEDT2KA5yS1lVR6M5gCAu/preview" width="900" height="480" allow="fullscreen"></iframe>

## Demo Explanation
Note: after each write, I show the updated DB state of the "item", "order", and "item_order" tables.

### Customer
In this demo, I add several of the initial items in the Items store into a shopping cart. The dropdown of each item has a max of 5 items to buy at one time.

Each item is added to the shopping cart, and I click "submit" to purchase the items. Once "submit" has been pressed, the shopping cart is cleared.

The userId used when purchasing a set of items is set by the user in the text area at the top of the Customer page.

Once the shopping cart has been submitted, a list of orders for the given userId is updated and displayed on the Customer page.

### Admin
In this part of the demo, I can show that the admin can see all orders for all users.

By clicking an "update" button for a given item, I can update the populated field of the given item. For example, when I want to update "Brooms", I only need to fill out the "Count" field, and the DB will be updated accordingly.

I can also "Delete" an item from the store. However, to preserve DB consistency, including the consistency of the Order and ItemOrder table, an item delete is a soft-delete, in which I set the "is_available" field for an item to `False`.

Lastly, I can add an item to the store using the "Add Item" form, in which a new item is inserted in the DB on a submit.

The item table is updated accordingly right after a DB update.

# Project Discussion
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


# Future Work/Conclusions
Overall, I thought this was a fun project, where I learn how to use Flask and SQLAlchemy. I also made practical data models with relations between each model. I also learned how to implement a more complex React frontend in order to submit REST API requests to the Python backend.

I thought about putting in Auth into this project, but considering that my next project is scoped for Auth, it wasn't necessary for this project. I'll use some of the knowledge learned here to help my IAM project, including the use of React Router for the OAuth 2.0 callbacks. 

This project took me about two weeks to complete in my remaining weeks at ObvioHealth, and I expect the IAM project to be at least 4 weeks considering that I'll be working at Disney by then.

Perhaps once I finish the Auth project, I'll retroactively put in auth here, but I may not.