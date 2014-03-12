---
layout: post
title:  "Ruby Array"
date:   2014-03-03 11:26:42
language: ruby
tags: free ruby coding resources array
categories: basics
repo: https://github.com/rubyonrailstutor/curriculum
---
<iframe width="640" height="360" src="//www.youtube.com/embed/X4gutclFQ7M?vq=hd1080" frameborder="0" allowfullscreen></iframe>

<h4><a href="{{ page.repo }}" target="_blank">follow along with the source code</a></h4>

```ruby
# http://ruby-doc.org/core-2.1.1/Array.html
# join a social pair programming class http://www.rubyonrailstutor.com

# how to view the first name ?
names = [ "jim", "john", "erik", "michelle"]
names[0]

# arrays are 'zero' index, ie, each name corresponds to an integer
# starting at 0

# how to view the last name ?
names[-1]

# whats the difference? 
names[3]

# how to change jim to jake ? 
names[0] = "jake"

# how to show the first 2 names ? 
names[0..1]

# what is .. ? 
# what do the brackets mean when written like names[ ] ?
# what is the purpose of an array ?

names = [ "jim", "john", "erik", "michelle"]

# Ruby Block
new_names = names.each do |n|
  p n.reverse
end

new_name = names.each {|name| name.reverse }

#will the below print true or false ?
names == new_names
actually_new_names = names.map do |n|
  n.reverse
end

new_names == actually_new_names
names = [ "john", "john", "erik", "michelle"]
john = names.select {|name| name == "john"}
john

# .pop is useful
names.pop

# .inject and .reduce are both useful
numbers = [ 1, 2, 3, 4]
numbers.inject(:+)
numbers.reduce(100) {|initial_value, n| initial_value + n }

# join a social pair programming class http://www.rubyonrailstutor.com
```
