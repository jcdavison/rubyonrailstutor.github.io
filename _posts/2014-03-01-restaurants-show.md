---
layout: post
title:  "Restaurants Show"
date:   2014-03-01 11:26:42
tags: restuarantsshow
categories: restuarantsshow
---

<iframe width="640" height="360" src="//www.youtube.com/embed/xhiqKVfpPBs?vq=hd1080" frameborder="0" allowfullscreen></iframe>


TEST DRIVE RESTAURANTS SHOW

GOALS

1. add test logic to controller
2. add view code to show a restaurant object

overview  'restaurants/1' is a place were we should be able to look at an object from the database.

git checkout -b show-restaurant

rails console => Restaurant.create name: "Mc Ruby on Rails"
note the id #


rm -rf test/
mkdir spec/requests | touch spec/requests/restaurant_spec.rb



create a restaurant object in the db.
visit restaurants/1


# modify requests/restaurant_spec.rb
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

rspec spec/requests/restaurants_spec.rb
# should be red

# modify restaurants_controller.rb

def show
  @restaurant = Restaurant.find_by_id params[:id]
  if @restaurant
    render :show
  else
    flash[:warning] = "sorry that restaurant doesn't exist"
    redirect_to root_path
  end
end


rspec spec/requests/restaurants_spec.rb
# should be green

# modify show.html.haml

.row
  .large-8.columns.large-centered
    %h1
      = @restaurant.name

# verify show in browser
