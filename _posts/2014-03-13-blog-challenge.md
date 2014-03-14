---
layout: post
title:  "Learn to fork, clone, edit, commit, push and use jekyll"
date:   2014-03-01 11:26:42
language: ruby
tags: captainslog
categories: challenges
repo: https://github.com/rubyonrailstutor/bengaltigers
screencast: "//www.youtube.com/embed/hQ8EO5xIXUg?vq=hd1080"
---

### Learn to fork, clone, edit, commit, push and use jekyll.




### http://rubyonrailstutor.github.io/bengaltigers

- note that I'm logged in as 'jcdavison', he is a friend of ours in the class whose account I use to highlight the point of view of you the student, vice my rubyonrailstutor github account.

> go to http://www.github.com/rubyonrailstutor/bengaltigers and click 'fork' in the top right corner, then follow the instructions to fork the repo to your own github profile

> then grab the url of the newly forked repo, clone it locally, make sure to clone your fork, not the original :)

> cd bengaltigers 

##### note, that for github pages, we will always work from the gh-pages branch, not master, if you need to `git checkout -b gh-pages` :)

> gem install jekyll

> jekyll serve -w

### navigate to http://localhost:4000/

> open 2014-03-05-cohort-session-log.md and add your feedback to my questions under your name

since we are using .md, that means "markdown" and you can use github flavored markdown syntax

https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

> save, git add . -A, git commit -m "your commit message"

> git push origin gh-pages


at this point, you will have pushed the branch to your own fork of the bengaltigers repository, which lives on the rubyonrailstutor github user account, we now want to issue a pull request.

https://help.github.com/articles/using-pull-requests

# IMPORTANT NOTE 

### development mode .config.yml looks like

```
name: RubyonRailsTutor.com Bengal Tigers Cohort Page
markdown: redcarpet
pygments: true
# url: http://rubyonrailstutor.github.io/bengaltigers
url: http://localhost:4000
```

### production mode .config.yml looks like

```
name: RubyonRailsTutor.com Bengal Tigers Cohort Page
markdown: redcarpet
pygments: true
url: http://rubyonrailstutor.github.io/bengaltigers
# url: http://localhost:4000
```

### So, when running this blog locally

edit config.yml 

make sure that url is set to http://localhost:4000/

you can use the # mark to comment out each different line.  when you push the code back to github,
make sure that you comment out the localhost line and uncomment the rubyonrailstutor.github.io/bengaltigers line
