# Intro to Rails

---

## Introduction to the Back End

**Frontend** refers to the interface a user interacts with. Basic languages include HTML, CSS, and JS. Many developers also use frameworks or libraries like Angular, Vue, Ember, and React. Focus is on user-facing aspects. Developers are limited to the languages browsers support.

**Backend** refers to everything that goes on behind the scenes on the servers. Focus is on application logic and data management. Does not rely on the browser, so you can run any language that takes HTTP requests, returns some HTML, and gets the job done on the backend. The browser just wants HTML/CSS/JS that is formatted correctly. Backend technologies interact with the frontend often by using APIs. Developers can build APIs that their frontend counterparts can use to connect client-side with server-side. Developers also need to be able to interact with **database management systems** (dbms), which involves understanding relational database systems/SQL or NoSQL databases like MongoDB. Frameworks also exist for backend (e.g., Flask, Django, Spring MVC, RoR, Meteor, Express). Typically, you would choose a backend framework based on what programming language it is written in and what features you will need to create.

**Servers**: you could run your own or use the cloud. Some popular server-side languages are Ruby, C#, Python, PHP, and Java. These languages can all pretty much do the same things, just with different syntax. Web apps and databases are deployed on a server. The server provides the app/database with data storage, computing resources, and different capabilities necessary for the application to run. Server examples include Apache and NGINX. Developers need a working knowledge of the Linux operating system.

**Fullstack** refers to both frontend and backend. Fullstack developers can create 'end-to-end' web apps. Some popular tech stacks include

- JAMstack (JS, APIs, and Markup)
- LAMP (Linux, Apache, MySQL, and PHP/Python)
- MEAN (MongoDB, Express, Angular, Node)

&nbsp;

## Frameworks

Instead of writing the same code and organizing the same folders over and over again with each app, developers created frameworks to do a lot of that heavy lifting. Frameworks help organize code and keep it clean. Ruby has frameworks that include Rails, Sinatra, and Padrino. Frameworks fit into three general categories: frontend, backend, and CSS/UI.

&nbsp;

---

## Basics of Rails

**MVC** - Model, Views, Controller = the backbone of Rails
**CRUD** - Create, Read, Update, Destroy = Rails makes this ridiculously easy
To create this, use scaffolds
Example
```Rails
rails g scaffold friends first_name:string last_name:string email:string phone:string twitter:string
```

thing:data-type

## Helpful Links

[Rails Guides](https://guides.rubyonrails.org)
