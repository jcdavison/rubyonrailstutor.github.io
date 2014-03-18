---
layout: post
title:  "Restaurantly Connecting Data to Client"
date:   2014-03-02 11:26:42
language: ruby
tags: free ruby coding resources MVC
categories: mvc
repo: https://github.com/rubyonrailstutor/restaurantly/tree/restaurant_ui
screencast: "//www.youtube.com/embed/1dvkowXmiio?vq=hd1080"
comments: true
---

#### modify config/application.rb

```
    config.generators do |generate|
      generate.helper false
      generate.assets false
      generate.view_specs false
    end
```

> rails g contoller restaurants show index new create edit update destroy

#### modify config/routes.rb

```
  resources :restaurants
```

> bundle exec rake routes

> git status

> git add . -A

#### pro tip add gs alias to ~/.bash_rc or ~/.bash_profile

```
  alias gs='git status'
```

> gs 

> git commit -m "UI framework in place"

> git status

> git checkout master

> git merge restaurant_ui
