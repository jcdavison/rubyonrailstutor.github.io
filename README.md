## Learn to code, for free.

### http://rubyonrailstutor.github.io

## JOIN A SOCIAL PAIR PROGRAMMING CLASS

### http://www.rubyonrailstutor.com


# john@rubyonrailstutor.com

to run this blog

> gem install jekyll
> git clone https://github.com/rubyonrailstutor/rubyonrailstutor.github.io.git
> cd rubyonrailstutor.github.io
> jekyll serve -w

### jekyll stuff

- to compile less files into css
- -x is the minify flag 
- the css file will get auto copied to site/assets/css 
- important, any changes made in assets/css wil get copied to site/assets
- so the less recomiple may or may not be necessary depending on purpose.

> lessc assets/less/main.less > assets/css/main.min.css -x

##### TODO SITE FEATURES

- comments?
- create a script that will publish issues to repo's that i'm a contributor on
- get the repo reviewed by a more senior coder, make sure i'm not crazy
- tdd the ajaxy cors stuff ? 
- create something to disable the buttons while 'in transit', this is such an interesting one, does it really matter, ie, will it really impact conversions ? 

##### TODO SITE CONTENT

- improve scripts on links that need it
- ajaxify a review object, with tests, and screencast
- ajaxify a tags has and belongs to many object, use angular, and screencast

### REPO FOR TUTORIAL CONTENT 

### https://github.com/rubyonrailstutor/restaurantly
