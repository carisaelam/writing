# Beginner–Friendly Basics: Rails Migrations

If you are new to Rails, understanding migrations can feel overwhelming and a bit opaque. This article is meant cover the basics and to simplify some of the primary components of migration. 

> We'll use a super simple [blog app](https://odin-blog-app-production.up.railway.app) deployed via [Railway](https://railway.app?referralCode=iwPZcx) as an example throughout this article.

### What is a Rails Migration?

Put simply, it is just a script that updates the schema of a database.

Each migration is like an updated version of your database.

When a Rails project is created, often one of the first things you need to do is to start creating a data model. In our case, a model for the articles that will populate the blog. Because this process involves the creation of a database table, you need to use migration to "change the schema" by setting it up.

Rails migration commands are simple and plain English, but they translate into SQL queries and get the job done under the hood.

### How Do You Perform a Migration?

Migrations can be triggered in a handful of different ways. This article will discuss two of them:

**1. By generating a model**
**2. By generating a standalone migration**

**1. Generating a _Model_**
No need to create all of the files and connections yourself, Rails handles most of the legwork for you.

For our blog example, running this command:

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

**`create    db/migrate/20240812123456_create_articles.rb`**: generates a migration file with a class named `CreateArticles`, which will ultimately create the `articles` table.

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
When you need to modify an existing data table or create a new schema change WITHOUT creating a new model, you can use the following command:

```CLI
$ rails generate migration CreateArticle
```

which will output something like this instead:

```CLI
$ rails generate migration CreateArticle
      invoke  active_record
      create    db/migrate/20240812123456_create_article.rb
```

As you can see, this command results in fewer things happening. Active Record is invoked, and an article migration file is created. `rails generate migration` does just what it says—it creates a migration file, not a model.

**When would I need to use `rails generate migration`?**

- Adding or removing columns from existing database tables
- Renaming a column or a table
- Changing the data type of a column
- Creating a join table
- Deleting ('dropping') a table from the database

**Am I done?**
No.
At this point, our changes have not actually been applied to the database schema. To do that, you would run:

```CLI
$ rails db:migrate
```

and voila! Your database table has been created, updated, deleted, etc.

**How do I know the migration was successful?**
Upon completion, the migration should output something like this to confirm success:

```CLI
==  CreateArticles: migrating =================================================
-- create_table(:articles)
   -> 0.0030s
==  CreateArticles: migrated (0.0030s) ========================================

```

**What if I mess up something?**
Made a mistake? No problem. Migrations are typically reversible, and it's almost as easy as `Ctrl–Z`! You simply run
`CLI $ rails db:rollback` and your migration effectively gets "undone." There's more to it than that under the hood, but as long as you have specified how each method should "reverse" itself, Rails handles the rest.

**Do I need to reserve the first column for a primary key?**
Typically, the first column in a table is reserved for the `id`, which serves as a unique identifier for each row of the table. By default, Rails automatically includes an auto-incrementing primary key `id` column to each table. So no need to do that yourself! You won't really "see" that anywhere in the code, you just have to hop on the Rails train and understand that it is happening behind the scenes.

### What Else Can Migrations Do?

Migrations are used in a ton of processes within a Rails app. While this article covers just the basics, here are some other things you can do with migrations:

- Create join tables
- Change current tables
- Change current columns
- Add column modifiers (`comment`, `default`, `limit`, etc.)
- Create foreign key columns to connect tables
- Execute custom SQL commands (for when the built-in functions just aren't enough)

### Summary
While we've just scratched the surface of what migrations can do, it's clear that Rails migrations can simplify the process of updating your database. Like [Active Record](https://dev.to/carisaelam/active-record-quick-start-46o5), migrations are designed to be as user-friendly as possible for developers while all of the complexity is handled behind the scenes. The result? We can get more done and focus on creating, not configuring. 

### Helpful Links

[The Odin Project](https://www.theodinproject.com)
LINK TO MY ACTIVE RECORD ARTICLE
[Rails Guide: Active Record Migrations](https://guides.rubyonrails.org/active_record_migrations.html)
