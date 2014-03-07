---
layout: post
title:  "Ruby on Rails Restaurantly #show controller action"
date:   2014-03-01 11:26:42
tags: show
language: ruby
categories: show
repo: https://github.com/rubyonrailstutor/restaurantly/tree/show-restaurant
---

<iframe width="640" height="360" src="//www.youtube.com/embed/xhiqKVfpPBs?vq=hd1080" frameborder="0" allowfullscreen></iframe>


#### CREATE RESTAURANTS#SHOW


#### add tests and application logic to controller


#### add view code to show a restaurant object



- overview  'http://localhost:3000/restaurants/:id' is a place were we should be able to look at an object from the database.

> git checkout -b show-restaurant

> rails console => Restaurant.create name: "Mc Ruby on Rails"

- note the Restaurant id #


> rm -rf test/
 
> mkdir spec/requests | touch spec/requests/restaurant_spec.rb

> visit http://localhost:3000/restaurants/:id

- note :id should be whatever the id from the restaurant object above was


> modify spec/requests/restaurant_spec.rb

```ruby

require 'spec_helper'

describe RestaurantsController do
  context "GET /restaurants/:id" do
    before do
      @restaurant = FactoryGirl.create :restaurant
    end

    context "resource exists" do
      subject {get "restaurants/#{@restaurant.id}"}
      it { expect(subject).to render_template(:show)}
    end

    context "resource doesn't exist" do
      subject {get "restaurants/#{@restaurant.id + 1}"}
      it { expect(subject).to redirect_to(:root) }
    end
  end
end

```

#### expect red


> rspec spec/requests/restaurants_spec.rb

> modify app/controllers/restaurants_controller.rb

```ruby

def show
  @restaurant = Restaurant.find_by_id params[:id]
  if @restaurant
    render :show
  else
    flash[:warning] = "sorry that restaurant doesn't exist"
    redirect_to root_path
  end
end

```

#### expect green 

> rspec spec/requests/restaurants_spec.rb 


> modify app/views/restaurants/show.html.haml

```haml
.row
  .large-8.columns.large-centered
    %h1
      = @restaurant.name
```

> verify & visit http://localhost:3000/restaurants/:id
