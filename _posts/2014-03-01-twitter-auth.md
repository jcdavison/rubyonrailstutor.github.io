---
layout: post
title:  "Twitter Based Login"
date:   2014-03-01 11:26:42
tags: twitterauth
categories: twitterauth
repo: https://github.com/rubyonrailstutor/restaurantly/tree/user-auth
---

<iframe width="640" height="360" src="//www.youtube.com/embed/qv41Bl4RhRI?vq=hd1080" frameborder="0" allowfullscreen></iframe>


#### SESSION & TWITTER AUTH

> git checkout -b user-auth

#### modify Gemfile.rb

```ruby
  gem 'omniauth'
  gem 'omniauth-twitter'
```



#### create sign_in partial

> touch app/views/layouts/_sign_in.haml

```haml
  .row
    .large-2.columns.large-centered
      - unless current_user
        = link_to "Sign Up/In", "/users/auth/twitter", class: "button small radius"
      - else
        = link_to "logout", destroy_user_session_path, method: "DELETE"
```

#### modify app/views/layouts/application.html.erb

```erb
  <%= render "layouts/sign_in" %>
```

#### create a new app on twitter

> visit https://apps.twitter.com/

#### description
reviews, reviews, reviews, reviews, reviews, reviews, reviews.
#### site
http://www.rubyonrailstutor.com
#### callback url
http://127.0.0.1/auth/twitter/callback
#### click allow this app to be used to sign in with twitter


#### set environmental variables in ~/.bash_profile

```sh
  export RESTAURANTLY_TWITTER_KEY='yourspecialkey'
  export RESTAURANTLY_TWITTER_SECRET='yourspecialsecret'
```

> source ~/.bash_profile

#### modify config/initializers/devise.rb

```ruby
  config.omniauth :twitter, ENV['RESTAURANTLY_TWITTER_KEY'], ENV['RESTAURANTLY_TWITTER_SECRET']
```

#### modify config/routes.rb

```ruby
  devise_for :users, :controllers => { :omniauth_callbacks => "users/omniauth_callbacks"}
```

#### modify app/models/user.rb

```ruby
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable, :omniauthable
```

> mkdir app/controllers/users | touch app/controllers/users/omniauth_callbacks_controller.rb


```ruby
  # props to @auser
  # the below is mangled a bit from https://leanpub.com/angularjs-rails

  class Users::OmniauthCallbacksController < Devise::OmniauthCallbacksController

    def twitter
      auth_hash = request.env["omniauth.auth"]
      uid = auth_hash["uid"]
      name = auth_hash["info"]["name"]
      handle = auth_hash["info"]["nickname"]
      auth = Authorization.find_by_provider_and_uid("twitter", uid)

      if auth
        user = auth.user
      else

        unless current_user
          unless user = User.find_by_name(name)
            user = User.create name: name, password: Devise.friendly_token[0,8],
              email: "default@mail.com", twitter: handle
          end
        else
          user = current_user
        end
        unless auth = user.authorizations.find_by_provider("twitter")
          auth = user.authorizations.build provider: "twitter", uid: uid
          user.authorizations << auth
        end

        auth.update_attributes uid: uid, token: auth_hash['credentials']['token'],
          secret: auth_hash["credentials"]['secret'], name: name, url: "https://twitter.com/#{name}"
      end

      if user
        sign_in_and_redirect user, :event => :authentication
      else
        redirect_to :new_user_registration
      end
    end

  end
```

#### resources

https://github.com/intridea/omniauth
https://github.com/arunagw/omniauth-twitter
