---
layout: post
title:  "koding.com ruby on rails setup"
date:   2014-03-01 11:26:42
language: ruby
tags: free ruby coding resources kodingsetup
categories: setup
repo: https://github.com/rubyonrailstutor/restaurantly/
---

<iframe width="640" height="360" src="//www.youtube.com/embed/iOLQkdok5tg?vq=hd1080" frameborder="0" allowfullscreen></iframe>

### TODO

### VERIFY GIT, INSTALL: RVM, RUBY, RAILS

### CREATE AND RUN A NEW APP


### verify git

> git --version

### navigate to koding.com, login with github

### isntall rvm, open a terminal 

> \curl -L https://get.rvm.io | bash -s stable

> source ~/.rvm/scripts/rvm

> rvm requirements

 -- this one requires your koding password, 
 -- it takes a while to run so be patient

### install ruby 2.1.1

> rvm install ruby 2.1.1 

> ruby -v

### suppress ri documentation installation

> touch ~/.gemrc

#### modify ~/.gemrc with the ace koding tool
#### we don't want docs installed, it is slow

{% highlight ruby %}
  gem: --no-document
{% endhighlight %}

### install rails 

> gem install rails

> mkdir apps

> cd apps

### create a new application call it what you want

> rails new restaurantly

> cd restaurantly

> rails server

#### navigate to the public url of your vm and verify things are good

#### you are ready to rock!!!

#### we will install posgresql on koding in another video,


### Mad Props to Lee @koding, he puts up with me, I'm demanding and un-abashed about it.

