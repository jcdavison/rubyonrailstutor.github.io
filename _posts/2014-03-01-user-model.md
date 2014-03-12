---
layout: post
title:  "Restaurantly User Authorization data models"
date:   2014-03-01 11:26:42
language: ruby
tags: free ruby coding resources userauth
categories: userauth
repo: https://github.com/rubyonrailstutor/restaurantly/tree/user-auth-models
---

<iframe width="640" height="360" src="//www.youtube.com/embed/YYRyg3aZWDQ?vq=hd1080" frameborder="0" allowfullscreen></iframe>


# purpose  - setup up user and authorization models to build prepare for twitter based login and session management.

1. generate user model
2. generate authorization model
3. create sql relationship between the two

> git checkout user-auth

#### modify Gemfile.rb

```
  #user auth
  gem 'devise', '3.0.0'
```


> bundle install

> rails generate devise:install

> rails generate devise user name:string email:string

> rake db:migrate

> verify in rails console

### generate authorization model

> rails g model Authorization provider:string uid:string user_id:integer token:string secret:string name:string url:string

> rake db:migrate



#### modify spec/models/authorization.rb

```
  context "required attributes" do
    context "uid" do
      subject {FactoryGirl.build :authorization, uid: nil}
      it { expect(subject.save).to be_false }
    end
  end
```

> bundle exec rake db:test:prepare

> rspec spec/models/authorization_spec.rb


#### expect red


#### modify app/models/authorizations.rb

```
  validates_presence_of :uid
```

> rspec spec/models/authorization_spec.rb


### expect green

```
  context "unique attributes" do
    context "uid" do
      before do
        FactoryGirl.create :authorization, uid: "12345"
      end
      subject {FactoryGirl.build :authorization, uid: "12345"}
      it { expect(subject.save).to be_false }
    end
  end
```

> rspec spec/models/authorization_spec.rb


#### expect red

#### modify app/models/authorizations.rb

```
  validates_uniqueness_of :uid
```

> rspec spec/models/authorization_spec.rb

#### expect green

> verify in rails console

#### create sql relationships

#### modify app/models/user.rb

```
  has_many :authorizations
```

#### modify app/models/authorizations.rb

```
  belongs_to :user
```

> verify in rails console

# resources
https://github.com/plataformatec/devise
