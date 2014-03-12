---
layout: post
title:  "Restuarantly #new #create"
date:   2014-03-01 11:26:42
language: ruby
tags: free ruby coding resources new create
categories: new
repo: https://github.com/rubyonrailstutor/restaurantly/tree/restaurants-new
screencast: "//www.youtube.com/embed/sxlV7yb6u3g?vq=hd1080"
---

### RESTAURANTS#NEW


1. add test structure for restaurants#new
2. create html front end required to submit new Restaurant object to the controller

> git checkout -b restaurants-new


> modify spec/requests/restaurants_spec.rb


```
  context "GET /restaurants/new" do
    subject {get "/restaurants/new" }

    it "renders new" do
      expect(subject).to render_template(:new)
    end
  end
```

>rspec spec/requests/restaurants_spec.rb


#### expect green


> modify app/controllers/restaurants_controller#new

```
  def new
    @restaurant = Restaurant.new
  end
```

> modify app/views/restaurants/new.html.haml

```
  .row
    .large-8.columns.large-centered
      = form_for @restaurant do |restaurant|
        = restaurant.text_field :name, placeholder: "name, eg 'mc ruby on rails'"
        = restaurant.submit "submit!", class: "button"
  .row
    .large-8.columns.large-centered
      %h3.subheader.center
        New Restaurantly Spots!
```

> verify in browser, visit http://localhost:3000/restaurants/new

### RESTAURANTS CREATE

1. create controller specs for POST to RESTAURANTS
2. Add front end html required to display successful creation of object and/or redirect

> modify /spec/requests/restaurants_spec.rb

```
  context "POST /restaurants" do
    context "complete params" do
      restaurant = {restaurant: {name: "mcrails"}}
      subject{ post "/restaurants", restaurant }
      it "redirects to show" do
        expect(subject).to redirect_to restaurant_path(id:1)
      end
    end

    context "incomplete params" do
      subject{ post "/restaurants", {}}
      it "redirects to new" do
        expect(subject).to redirect_to(new_restaurant_path)
      end
    end
  end
```


> rspec spec/requests/restaurants_spec.rb


### expect red


> modify app/controllers/restaurants_controller.rb


```
  def create
    name = params[:restaurant][:name] if params[:restaurant]
    @restaurant = Restaurant.new name: name
    if @restaurant.save
      flash[:success] = "#{@restaurant.name} created"
      redirect_to restaurant_path @restaurant
    else
      flash[:warning] = @restaurant.errors.inspect
      redirect_to new_restaurant_path
    end
  end
```


> rspec spec/requests/restaurants_spec.rb


### should be green
