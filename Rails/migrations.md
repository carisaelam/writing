# Beginner–Friendly Basics: Rails Migrations

### Helpful terms

**_Schema_**: structure of a database
**SQL queries**: "asking" something from a database

> We'll use a super simple [blog app](https://odin-blog-app-production.up.railway.app) deployed via [Railway](https://railway.app?referralCode=iwPZcx) as an example throughout this article.

### What is a Rails Migration?

Put simply, it is just a script who's job is to update the **_schema_** of a database.

Each migration is like an updated version of your database.

When a Rails project is created, often one of the first things we need to do is to start creating a data model. In our case, a model for the articles that will populate the blog. Because this process involves the creation of a database table, we have to use migration to "change the schema" by setting it up.

Rails migration commands are simple and plain English, but they translate into SQL queries and get the job done under the hood.

### How do you perform a migration?

Migrations can be triggered in a handful of different ways. This article will discuss two of them:

**1. By generating a model**
**2. By generating a standalone migration**

**1. Generating a _Model_**
No need to create all of the files and connections yourself, Rails handle most of the legwork for you.

In the case of our blog, running this command:

```CLI
$ rails generate model Article
```

would return something like this:

```CLI
$ rails generate model Article
      invoke  active_record
      create    db/migrate/20240812123456_create_articles.rb
      create    app/models/article.rb
      invoke    test_unit
      create      test/models/article_test.rb
      create      test/fixtures/articles.yml
```

Let's break that down.
**`invoke active_record`**: as it implies, this brings Active Record into the picture

**`create    db/migrate/20240812123456_create_articles.rb`**: creates a Ruby class with the plural form of your method name prepending with "create"

```Ruby
class CreateArticles < ActiveRecord::Migration[7.2]
  def change
    create_table :articles do |t|
      t.timestamps
    end
  end
end
```

**`create    app/models/article.rb`**: creates your model

```Ruby
class Article < ApplicationRecord
end
```

...and then creates some files that are applicable for testing.

**2. Generating a standalone _Migration_**
For times when you are just modifying an existing data table or other times when you don't need to generate a new model, you can use the following command:

```CLI
$ rails generate migration Article
```

which will output something like this instead:

```CLI
$ rails generate migration Article
      invoke  active_record
      create    db/migrate/20240812123456_article.rb
```

As you can see, this command results in fewer things happening. Active Record is invoked, and an article migration file is created. Notice that in this case, the class name is simply `Article`, not `CreateArticle`. You could go into the migration file and manually add the methods you would need.

**When would I need to use `rails generate migration`?**

- Adding or removing columns from existing database tables
- Renaming a column or a table
- Changing the data type of a column
- Creating a join table
- Deleting ('dropping') a table from the database

**Am I done?**
No.
Right now, your changes are have not actually been applied to the database schema. To do that, you would run

```CLI
$ rails db:migrate
```

and voila! Your database table has been created, updated, deleted, etc.

**How do I know the migration was successful?**
Upon completion, the migration should output something like this: 
```CLI
==  CreateArticles: migrating =================================================
-- create_table(:articles)
   -> 0.0030s
==  CreateProducts: migrated (0.0030s) ========================================

```


**What if I mess up something?**
Undo! Migrations are typically reversible, and it's almost as easy as `Ctrl–Z`! You simply run
`CLI $ rails db:rollback` and your migration effectively gets "undone." There's more to it than that under the hood, but as long as you have specified how each method should "reverse" itself, Rails handles the rest.

### What else can migrations do?

**Do I need to reserve the first column for a primary key?**
Typically, the first column in a table is reserved for the "id" or for something that will serve as a completely unique identifier for each row of the table. By default, a newly created database table in Rails will automatically include an auto-incrementing primary key "id" column. So no need to do that yourself! You won't really "see" that anywhere in the code, you just have to hop on the Rails train and understand that it is happening behind the scenes.

**What else can you use migrations for?**
Migrations are used in a ton of processes within a Rails app. This goes a bit beyond the scope of this article, but here are several other operations that use migrations: 
- Creating join tables 
- Changing current tables
- Changing current columns
- Adding column modifiers (`comment`, `default`, `limit`, etc.)
- Creating foreign key columns to connect tables
- Execute custom SQL commands (for when the built-in functions just aren't enough)



### Helpful Links

[The Odin Project](https://www.theodinproject.com)
LINK TO MY ACTIVE RECORD ARTICLE
[Rails Guide: Active Record Migrations](https://guides.rubyonrails.org/active_record_migrations.html)
