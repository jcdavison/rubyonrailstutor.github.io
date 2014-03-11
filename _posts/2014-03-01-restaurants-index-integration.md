---
layout: post
title:  "Restaurantly #index & integration"
date:   2014-03-01 11:26:42
language: ruby
tags: free ruby coding resources integrationtesting
categories: integration
repo: https://github.com/rubyonrailstutor/restaurantly/tree/restaurants-index
---

<iframe width="640" height="360" src="//www.youtube.com/embed/Mo5j8eEbwbo?vq=hd1080" frameborder="0" allowfullscreen></iframe>

### RESTAURANTS INDEX

> git checkout -b restaurants-index

> modify spec/requests/restaurant_spec.rb

~~~ ruby
  context "GET /" do
    subject { get "/" }
    it "renders index" do
      expect(subject).to render_template(:index)
    end
  end
~~~ 

> modify app/controllers/restaurants_controller.rb

~~~ ruby
  def index
    @restaurants = Restaurant.all
  end
~~~ 

> rspec spec/requests/restaurants_spec.rb

### should be green


> modify index.html.haml

~~~ haml
  .row
    .large-8.columns.large-centered
      %h3.subheader.center
        Restaurantly Spots!
  .row
    .large-8.columns.large-centered
      - @restaurants.each do |restaurant|
        %h5.subheader
          = restaurant.name
~~~ 

> verify in browser, visit http://localhost:3000/index.html.haml


### INTEGRATION RESTAURANTS#EDIT

> git checkout -b restaurant-edit-integration

> modify spec/features/restaurants_spec.rb

~~~ ruby
  describe "edit links work" do
    context "displays ", :driver => :selenium do
      it "Restaurantly Spots!" do
        visit '/restaurants/new'
        fill_in 'restaurant_name', with: "mc ruby"
        click_button 'submit!'
        visit '/'
        click_link 'edit'
        fill_in 'restaurant_name', with: "mc rails"
        click_button 'update'
        expect(page).to have_content 'mc rails'
      end
    end
  end
~~~ 

> rspec spec/features/restaurants_spec.rb


### expect green


~~~ ruby
  describe "destroy links work" do
    context "displays ", :driver => :selenium do
      it "Restaurantly Spots!" do
        visit '/restaurants/new'
        fill_in 'restaurant_name', with: "mc ruby"
        click_button 'submit!'
        expect(page).to have_content 'mc ruby'
        visit '/'
        click_link 'destroy'
        expect(page).to have_no_content 'mc ruby'
      end
    end
  end
~~~ 

> rspec spec/features/restaurants_spec.rb


### expect green
