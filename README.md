## Local setup


* install Jekyll by executing following in terminal
  
  `gem install bundler jekyll`
  
* Clone/download the repo
* Navigate to repo via terminal and execute following

  `bundle install`

  `bundle exec jekyll serve --livereload`
  
  this will start a local server on port `4000`. Go to a browser and access http://localhost:4000
  
* To only build the project execute `bundle exec jekyll build` and the project will get built inside `_site` folder
  
## Netlify setup


* When setting up this repo on netlify, make sure to have following as deployment settings

    **Build command:** `jekyll build`

    **Publish directory:** `_site/`