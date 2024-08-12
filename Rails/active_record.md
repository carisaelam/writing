# Active Record

#### It's all about the data

It is important to set up a simple, logical data model for your application, and it is important to plan this out _before_ you get too far into the project. Messy data structures lead to headaches and wasted time in the future.

Rails handles data through **_Active Record_**—an interface that connects your application with its database.

> After having just deployed my first application to the web via the [Railway hosting provider](https://railway.app?referralCode=iwPZcx), I am excited to learn how to actually access, monitor, and alter the database in a meaningful way.

#### What is Active Record?

Active Record is actually one of the seven gems that make up Rails. It is an **_Object-Relational-Mapping (ORM)_** tool that is responsible for the database.
&nbsp;

#### What does Active Record do?

1. Takes the app data from the rows and columns in your database
2. Allows you to interact with the data as a Ruby object

It is like magic!—like a little middleman between you and your database that handles writing and executing all of the queries you would otherwise have to type out yourself. Instead, you just give it something written in Ruby (which is WAY easier to write, read, and understand IMHO), and it translates that into the language of your database and returns the thing you're looking for.

**_So how does Active Record know what kind of database you are using?_**
You basically give Active Record some basic information about your database via the `config/database.yml` file, and it handles the rest. That means if you end up switching databases later on, you should theoretically only have to change the configuration info. Is this what they mean by "The Rails Way"? Seems pretty nice honestly.

> **_Active Record vs Active Model_**
> Both are part of the "Model" in MVC.
> `Active Model`: used with Ruby objects that don't need to be stored in a database
> `Active Record`: used with Ruby objects that DO need to be store in a database

We'll use my super simple [blog app](https://odin-blog-app-production.up.railway.app) deployed via [Railway](https://railway.app?referralCode=iwPZcx) as an example.

Information about the articles on my blog are stored in a database table called `articles`. The model used to access that data is called `article`, in keeping with the [Rails singular/plural configuration](https://dev.to/scrabill/singular-or-plural-a-cheatsheet-for-ruby-on-rails-generators-4cb8).

**Article Model**

```Ruby
class Article < ApplicationRecord
  ...
end
```

The model is simply a Ruby object that inherits from `ApplicationRecord` which in turn inherits from `ActiveRecord`.

```Ruby
class ApplicationRecord < ActiveRecord::Base
  primary_abstract_class
end
```

So there's the connection! And it is easy to see thanks to Ruby.

#### Naming conventions

This isn't just to make your code look pretty. Rails emphasizes _"convention over configuration"_ to help lighten the load on developers. Instead of having to write out lots of lines of configuration code to get your application to work, just hop onboard the Rails wagon 🚃 and do it like they say to.

Rails will automatically pluralize your model's class names. In my case, the model was `class Article`, so the database table is called `articles` as you can see in my `articles` controller:

```Ruby
class ArticlesController < ApplicationController
 def index
    @articles = Article.all
  end

  def show
    @article = Article.find(params[:id])
  end

  # etc...
end
```

> Rails uses a method called `Active Support` to accomplish this, so it is not magic, nor is it simply adding a period on at the end. (e.g., `Person` gets mapped to `people` automatically.)

#### Creating an Active Record model

When you run `rails new` and create a new Rails app, the `ApplicationRecord` class gets created and placed in the `app/models` directory. As we saw before, `ApplicationRecord` inherits from `ActiveRecord::Base`. So to create a new Active Record model, you just create a new class that inherits from `Application Record`. Remember to make your class name singular!

```Ruby
class Article < ApplicationRecord
end
```

When you do this, Rails creates a `Article` model that is mapped to a `articles` table in the database. Each column of the table will be mapped to an attribute of the `Article` class. An instance of the `Article` class represents a single row in the `articles` database table.

**_But where is the table? Is it created already?_**
Rather than creating the table via a `CREATE TABLE` SQL statement that explicitly defines all of the column headers and their types, you will just use an `Active Record Migration` on the command line.

```CLI
$ bin/rails generate migration CreateArticles title:string body:text
```

```Ruby
class CreateArticles < ActiveRecord::Migration[7.2]
  def change
    create_table :articles do |t|
      t.string :title
      t.text :body

      t.timestamps
    end
  end
end
```

`bin/rails db:migrate`

Another example of hopping on the Rails wagon 🚃 and just letting it do its thing.

&nbsp;

#### CRUD and Active Record

Rails is built around the idea that most applications operate on data in four ways: **C**reating, **R**eading, **U**pdating, and **D**eleting (CRUD). This is so ingrained in Rails that when you create a new Active Record, Rails automatically provides a [set of built-in methods](https://guides.rubyonrails.org/active_record_querying.html) to make it super easy to perform CRUD operations.

**🚃 Hop Aboard!**
Each of these methods result in the creation and execution of SQL statements behind the scenes. Rails also provides plain-English ways of accessing these methods, making it _even easier_ to connect with your records.

**What you see**: `articles = Article.all`

**What goes on behind the scenes**: `SELECT "articles".* FROM "articles"`

&nbsp;

#### Migrations

When you need to make changes to the structure of your database, you use a **migration**.

## Helpful Links

[The Odin Project](https://www.theodinproject.com)
[Rails Guides: Active Record Basics](https://guides.rubyonrails.org/active_record_basics.html)

---

<div class="connect__container">
  <h4>Connect with me!</h4>

  <div class="pic__and__links__container">
    <img class="profile__pic" src="assets/profile_pic.png">
    <div class="connect__links">
      <a href="https://github.com/carisaelam">GitHub</a>
      <a href="www.linkedin.com/in/carisa-elam-097368239">LinkedIn</a>
    </div>
  </div>
</div>

<style>
.connect__container{
    display: flex;
    flex-direction: column;
}

a {
  font-weight: bold;
}

.pic__and__links__container {
  display: flex;
  gap: 2rem;
  margin-top: 1rem;
}

.profile__pic {
  max-width: 7rem;
  border-radius: 100%;
}

.connect__links {
  display: flex;
  flex-direction: column;
  gap: .5rem;
  justify-content: center;
}
</style>

```

```
