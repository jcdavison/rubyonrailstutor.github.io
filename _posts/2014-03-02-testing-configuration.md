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

#### modify Gemfile

{% highlight ruby %}
  gem 'selenium-webdriver'
  gem 'database_cleaner', '~> 1.2.0'
{% endhighlight %}

> bundle install

> mkdir spec/support/ | touch spec/support/database_cleaner.rb

{% highlight ruby %}
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
{% endhighlight %}

#### modify app/assets/javascripts/application.js


{% highlight javascript %}
  # remove //= turbolinks
{% endhighlight %}

> touch app/assets/stylesheets/restaurants.css.scss


#### modify app/assets/stylesheets/restaurants.css.scss

{% highlight css %}
  .center {
    text-align:center;
  }
{% endhighlight %}

#### modify config/routes.rb

{% highlight ruby %}
  root to: "restaurants#index"
{% endhighlight %}
