---
layout: post
title:  "MAC OSX Ruby on Rails Development Setup"
date:   2014-03-25 11:26:42
language: english
tags: development tools
categories: rubyonrailstutor
comments: true
---
Setting up and configuring your development environment at first hurts, causes problems and stress.  I won't say there isn't some significant pain involved in installing and getting everything dialed in.  

### I've felt the same pain, I will help minimize it for you.  

I can guarantee there will be hassles, I can guarantee that I won't know everything, I can guarantee that I will become part of the solution, not the problem.

### TAKE MAXIMUM OWNERSHIP OF YOUR MACHINE

In all cases in coding and dev setup, read instructions carefully and follow the details as written, understand that tutorials are inherently brittle and that developing your intuition is of utmost power.

At a mininum, to function well as a professional, a student and a remote pair programming coder, I consider the following tools a must. I don't necessarily state that you install and configure everything as I do, but you must in some way shape or form possess the capability of each tool. 

The following information is a reference of how I have done things and how to verify setup on my own system, depending on any number of control factors, things could be different on your side.

## DO BEFORE ANYTHING ELSE IF ON MAC OSX !!!!

## INSTALL XCODE, COMMAND LINE TOOLS THEN HOMEBREW

### XCODE

Capability: On mac osx, to get the right level of system access, you must download xcode and install the command line tools package.  

<a href="https://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12">Xcode in Itunes</a>

The download has been known to take many hours, so be patient. Once you have it installed, install the command line tools.

> xcode-select --install

<img src="{{ site.url }}/images/cohorts/xcode.png">


### HOMEBREW aka BREW

Capability: On mac osx, to be able to install interesting software from the internet by issuing terminal commands.  Brew is very useful.

> brew --version

<img src="{{ site.url }}/images/cohorts/brew.png">


#### special note about brew

If you are on mac osx, install brew before you install lots of other stuff and use brew whenever tutorials or installation instructions say you can use it.  You also should make sure to set your osx system software settings to 'Allow apps downloaded from: Anywhere' in order for lots of this stuff to run correctly.

<img src="{{ site.url }}/images/cohorts/brewb.png">

<a href="http://brew.sh/" target="new">http://brew.sh/</a>


### RVM or RBENV

Capability: Allow for multiple versions of ruby to be installed and run in different projects. 

I use RVM. It works, you know you have rvm installed correctly when;

> rvm --version

<img src="{{ site.url }}/images/cohorts/rvm.png">

<a href="http://rvm.io/rvm/install" target="new">http://rvm.io/rvm/install</a>

or 

<a href="https://github.com/sstephenson/rbenv" target="new">https://github.com/sstephenson/rbenv</a>

### RUBY

Capability: To be able to run basic flavors of ruby.

Once you have rvm/rbenv installed, you can install all kinds of rubies.  Mac OSX ships with ruby 1.8 already, that is not good enough for our purposes, you need to install rvm or rbenv and install more current version of ruby, like ruby 2.1. You know you are good to go when,

> ruby -v

<img src="{{ site.url }}/images/cohorts/ruby.png">

<a href="http://rvm.io/rubies/installing" target="new">http://rvm.io/rubies/installing</a>

### RAILS

Capability: To be able to build rails application structure with 'rails new' command.

> rails -v

<img src="{{ site.url }}/images/cohorts/rails.png">

<a href="http://rubyonrails.org" target="new">http://rubyonrails.org</a>

If you have rvm and ruby installed properly, installing rails 'should' be as easy as...

> gem install rails


### CODE EDITOR


Capability: To be able to open and edit files/applications from the command line.

Install sublime, or textmate, or anything that makes sense, as long as you can code quickly, set tabs, search for files and have nested panes of code.

I use VIM when I code and sublime mostly to teach.  The one detail that is very important is to ensure you configure sublime to be accessible from the command line.  Sublime is great software, if you use it please pay for it.  Having constant popups while you code interrupts your flow.

> sublime .

<img src="{{ site.url }}/images/cohorts/sublime.png">

<a href="http://www.sublimetext.com/">http://www.sublimetext.com/</a>

A great tutorial on how to configure sublime to be opened from the command line.

<a href="https://gist.github.com/artero/1236170">https://gist.github.com/artero/1236170</a>


## COLLABORATION TOOLS

### GIT

Capability: To be able to put applications under version control and push/pull/edit/clone/fork code at github.

It isn't enough to just have git installed, in order to interact quickly with github, you must configure you ssh keys to work properly as well. On mac osx, homebrew is a good tool for installing git and lots of other programms. Please do not get any crazy ideas about using a GUI git tool, understanding git at the command line is probably the single most important skill to being able to learn and produce software in a collaborative context.

> git --version

> ssh -T git@github.com

<img src="{{ site.url }}/images/cohorts/git.png">

<a href="https://help.github.com/articles/set-up-git" target="new">https://help.github.com/articles/set-up-git</a>

### FLOOBITS

Capability: Collaborative real time code sharing with audio and video integration.

Rubyonrailstutor.com wouldn't be possible without floobits... 

Signup for a <a href="http://flootbits.com/" target="new">floobits.com</a> account and send it to me. 

Make sure you have a g+ account as well as we need it for audio/video integration.

Also, setup sublime to work with floobits and if you can get flootty installed, you will be really ready to rock and ahead of like 80% of all remote pair programming types.

<a href="https://floobits.com/help/plugins/sublime">https://floobits.com/help/plugins/sublime</a>

<a href="https://github.com/Floobits/flootty">https://github.com/Floobits/flootty</a>

notes about remote pair progamming

1. A large monitor is very useful, I use a 22" acer hd.

2. A decently fast, speed > 1.5 MBS internet connection is very useful.

3. A good headset is also very useful, I use the <a href="http://shop.steelseries.com/us/audio/steelseries-siberia-v2-full-size-usb-headset.html" target="new">SteelSeries Siberia V2</a>, they aren't the cheapest headset but neither the most expensive.   If you are serious about this process, you need to be serious about your tools.  Having a good headset makes a binary difference in the quality of our sessions.

<img src="{{ site.url }}/images/cohorts/headphones.png">

### SIZEUP (or whatever window management tool you choose)

Capability: Use keyboard commands to dock, move and maximize windows in mac osx. 

Please respect how important it is to become a fast coder, the more you use your mouse, the slower you will be.  Using your mouse to control the position of windows in your os is a very cerebrally laborious task, use hotkeys.  Sizeup is paid, along with the headphones I use, it is one of the few expenses on this page of amazing free tools.

Watch this video of me quickly cycling through and moving windows around. <a href="http://quick.as/dv6dszmo" target="new">http://quick.as/dv6dszmo</a>

<a href="https://www.irradiatedsoftware.com/sizeup/" target="new">https://www.irradiatedsoftware.com/sizeup/</a>
