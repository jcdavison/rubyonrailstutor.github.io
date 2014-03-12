---
layout: post
title:  "Restaurantly Restaurant Data Model"
date:   2014-03-02 11:26:42
language: ruby
tags: free ruby coding resources rails data models
categories: datamodels
repo: https://github.com/rubyonrailstutor/restaurantly/tree/restaurant_model
---


<iframe width="640" height="360" src="//www.youtube.com/embed/9yxyw0SMMCs?vq=hd1080" frameborder="0" allowfullscreen></iframe>

<h4><a href="{{ page.repo }}" target="_blank">follow along with the source code</a></h4>

> git checkout -b restaurant_model

> rails g model restaurant name:string address:string 

#### pro tip setup 'be' in ~/.bash_profile or ~/.bashrc

```
  alias be='bundle exec'
```

### then type source ~/.bash_profile or ~/.bashrc

> be rake db:migrate

> be rake db:test:prepare

> sublime .

#### modify spec/spec_helper.rb

```
  config.expect_with :rspec do |c|
    c.syntax = :expect
  end
```

#### modify spec/models/restaurant_spec.rb

```
  require 'spec_helper'

  describe Restaurant do
    subject(:restaurant) { FactoryGirl.build(:restaurant, name: nil)}
    it {expect(restaurant.valid?).to be_false}
  end
```

#### expect red

> rspec spec/models/restaurant_spec.rb

#### modify app/models/restaurant.rb

```
  class Restaurant < ActiveRecord::Base
    validates_presence_of :name
  end
```

#### expect green

> rspec spec/models/restaurant_spec.rb

> rails console

> Restaurant.new

> resturant = Restaurant.new(name: "john's cafe")

> restaurant.save

> Restaurant.count

> Restaurant.last
