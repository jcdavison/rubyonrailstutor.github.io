---
layout: post
title:  "Restaurantly#edit #update #destroy controller actions"
date:   2014-03-01 11:26:42
language: ruby
tags: free ruby coding resources edit update destroy 
categories: edit
repo: https://github.com/rubyonrailstutor/restaurantly/tree/restaurants-edit
---

<iframe width="640" height="360" src="//www.youtube.com/embed/juedMSbXdEc?vq=hd1080" frameborder="0" allowfullscreen></iframe>


### RESTAURANTS#EDIT

> git checkout -b restaurants-edit

### modify spec/requests/resaurants_spec.rb

```ruby
  context "GET /restaurants/:id/edit" do
    before do
      @restaurant = FactoryGirl.create :restaurant
    end

    context "resource exists" do
      subject { get "/restaurants/#{@restaurant.id}/edit" }
      it {expect(subject).to render_template(:edit)}
    end

    context "resource doesn't exist" do
      subject {get "restaurants/#{@restaurant.id + 1}/edit"}
      it { expect(subject).to redirect_to(:root) }
    end
  end
```

> rspec spec/requests/restaurant_spec.rb


### expect green and red

> modify app/controllers/restaurants_controller.rb

```ruby
  def edit
    @restaurant = Restaurant.find_by_id params[:id]
    if @restaurant
      render :edit
    else
      redirect_to root_path
    end
  end
```

> modify app/views/restaurants/edit.html.haml

```haml
  .row
    .large-8.columns.large-centered
      = form_for @restaurant do |restaurant|
        = restaurant.text_field :name
        = restaurant.submit "update", class: "button"
```

> modify index.html.haml

```ruby
  = link_to "edit", edit_restaurant_path(restaurant)
```

> modify spec/requests/resaurants_spec.rb

```ruby
  context "PUT /restaurants/:id" do
    context "complete params" do
      before do
        @restaurant = FactoryGirl.create :restaurant
        @restaurant_info = {id: @restaurant.id, restaurant: {name: "mcrails"}}
      end
      subject{ put "/restaurants/#{@restaurant.id}", @restaurant_info }
      it { expect(subject).to redirect_to restaurant_path(id:1) }
    end

    context "incomplete params" do
      subject{ put "/restaurants/1", {id: 1} }
      it { expect(subject).to redirect_to root_path }
    end
  end
```

> rspec spec/requests/restaurant_spec.rb


> modify app/controllers/restaurants_controller.rb

```ruby
  def update
    @restaurant = Restaurant.find_by_id params[:id]
    if @restaurant
      @restaurant.update_attributes(name: params[:restaurant][:name])
      flash[:success] = "Name Updated!"
      redirect_to restaurant_path @restaurant
    else
      flash[:alert] = "Houston, we have a problem"
      redirect_to root_path
    end
  end
```

> modify spec/requests/resaurants_spec.rb

```ruby
  context "DELETE /restaurants/:id" do
    context "complete params" do
      before do
        @restaurant = FactoryGirl.create :restaurant
      end
      subject{ delete "/restaurants/#{@restaurant.id}"}
      it { expect(subject).to redirect_to root_path }
    end
  end
```

> modify app/controllers/restaurants_controller.rb

```ruby
  def destroy
    @restaurant = Restaurant.find_by_id params[:id]
    @restaurant.destroy
    redirect_to root_path
  end
```

> modify index.html.haml

```ruby
  = link_to "destroy", restaurant_path(restaurant), method: :delete
```

> verify in browser, visit http://localhost:3000/
