---
layout: post
title:  "Restaurantly Application setup"
date:   2014-03-02 11:26:42
language: ruby
tags: free ruby coding resources railssetup
categories: setup
repo: https://github.com/rubyonrailstutor/restaurantly/tree/setup
screencast: "//www.youtube.com/embed/haeJMoZFVrc?vq=hd1080"
comments: true
---

# HOW TO SETUP RESTAURANTLY

#### view the code


#### https://github.com/rubyonrailstutor/restaurantly/tree/setup


> ruby -v

> rails -v

> rails new restaurantly

> cd restaurantly

> git init

> git status

> git commit -m "init"

> git checkout -b setup

> git status

> subl .


#### update Gemfile


```
  source 'https://rubygems.org'

  # application gems
  gem 'rails', '4.0.2'
  gem 'pg', '~> 0.17.1'
  gem 'thin', '~> 1.6.1'

  # assets and views
  gem 'sass-rails', '~> 4.0.0'
  gem 'uglifier', '>= 1.3.0'
  gem 'coffee-rails', '~> 4.0.0'
  gem 'therubyracer', platforms: :ruby
  gem 'jquery-rails'
  gem 'haml-rails'
  gem 'foundation-rails'

  group :test, :development do
    gem 'quiet_assets'
    gem "rspec-rails", "~> 2.14.1"
    gem 'factory_girl_rails', '4.2.1'
    gem 'capybara', '~> 2.2.1'
    gem 'pry'
    gem 'pry-debugger'
  end

  group :doc do
    gem 'sdoc', require: false
  end
```

> bundle install

> rails generate rspec:install

> rails g foundation:install
> Y

#### update config/database.yml

```
  development:
    adapter: postgresql
    encoding: unicode
    database: restaurantly_dev
    pool: 5
    host: localhost
    port: 5432

  test:
    adapter: postgresql
    encoding: unicode
    database: restaurantly_test
    pool: 5
    host: localhost
    port: 5432
```

> bundle exec rake db:create

> rails server

#### visit http://localhost:3000/ in a web broswer
