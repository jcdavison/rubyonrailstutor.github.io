---
layout: post
title:  "Restaurantly Testing Configuration"
date:   2014-03-02 11:26:42
language: ruby
tags: free ruby coding resources testingconfiguration
categories: testingconfig
repo: https://github.com/rubyonrailstutor/restaurantly/tree/test-setup
---


<iframe width="640" height="360" src="//www.youtube.com/embed/JNEMXq3srzM?vq=hd1080" frameborder="0" allowfullscreen></iframe>

<h4><a href="{{ page.repo }}" target="_blank">follow along with the source code</a></h4>

#### modify Gemfile

```
  gem 'selenium-webdriver'
  gem 'database_cleaner', '~> 1.2.0'
```

> bundle install

> mkdir spec/support/ | touch spec/support/database_cleaner.rb

```
  # props to @avdi
  # http://devblog.avdi.org/2012/08/31/configuring-database_cleaner-with-rails-rspec-capybara-and-selenium/

  RSpec.configure do |config|

    config.before(:suite) do
      DatabaseCleaner.clean_with(:truncation)
    end

    config.before(:each) do
      DatabaseCleaner.strategy = :transaction
    end

    config.before(:each, :js => true) do
      DatabaseCleaner.strategy = :truncation
    end

    config.before(:each) do
      DatabaseCleaner.start
    end

    config.after(:each) do
      DatabaseCleaner.clean
    end

  end
```

#### modify app/assets/javascripts/application.js


```
  # remove //= turbolinks
```

> touch app/assets/stylesheets/restaurants.css.scss


#### modify app/assets/stylesheets/restaurants.css.scss

```
  .center {
    text-align:center;
  }
```

#### modify config/routes.rb

```
  root to: "restaurants#index"
```
