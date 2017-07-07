# Lunch-learn July 7th, 2017

## Links:

Rails install: https://gorails.com/setup/osx/10.12-sierra

Fae CMS: https://github.com/wearefine/fae

Heroku Documentation: https://devcenter.heroku.com/articles/getting-started-with-rails5

Fae CMS (Docs): https://www.faecms.com/documentation/

### Base configuration
1. Install Rails using the first link.
2. use `rails new fae --database=postgresql` to create a new application named Fae. Navigate to this directory.
3. In your terminal using either nano, vi, or vim edit `Gemfile`. 
4. Add `gem 'fae-rails'` anywhere in the document (I like to add it at the top of the doc)
5. Run Bundle install _This is required, I've done it in advance so as not to take 30 minutes installing stuff_
6. Run `rails g fae:install`
7. Next run `rake db:create` and `rake db:migrate fae:seed_db`. These two commands need to be run individually. The first will create the database, the second will create the tables & put the entries that Fae needs into it. 

### Pushing to heroku:
If you've ever pushed to heroku it's the exact same process but you do not need a procfile! For those who are unfamiliar please check: https://devcenter.heroku.com/articles/getting-started-with-rails5 and: https://www.faecms.com/documentation/installation-index#heroku for more information.
Key things to note:
* Heroku will only allow Postgres as the database (hence why we specified Postgresql in step 2).
* In order to push up to heroku you must have run the above commands & bundle has to install sucessfully. (if you get an error about a MagickWand it's a version mismatch, follow the first answer here: https://stackoverflow.com/questions/39494672/rmagick-installation-cant-find-magickwand-h) 
* Once the app is on heroku run: 
```
heroku run rake db:migrate
heroku run rake fae:seed_db
```

## Misc Notes
_Pushing to heroku takes a bit of time_

A 1-1 Rails to Node:
`npm install` = `bundle install`
`npm install -g` = `gem install`
`rails s` = `npm start`

General rails commands:
* `rails g controller [name]`/`rails generate controller [name]`: similar to `yo kraken:controller [name]`. Generates a new controller with `[name]`. Similarly controller can be replaced with model, or view. This will also generate a migration for you to use for database storage.
* `rake`: automates tasks for you
* `rake db:create`: Creates the databases that have been created.
* `rake db:migrate`: runs all migrations that have been created (from `rails g`).
* `rails g fae:install`: installs the Fae Gem and all the things it requires.
* `rake assets:precompile`: precompiles the assets so they can be served faster
