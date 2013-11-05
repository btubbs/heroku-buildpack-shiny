Heroku Buildpack Shiny
===========================

This is a Heroku buildpack for the [Shiny](http://www.rstudio.com/shiny/) web
framework that runs on [R](http://www.r-project.org/).

Check it out: http://shiny-example-1.herokuapp.com/.  The source for that is at
https://github.com/btubbs/shiny-example-1.

Instructions
------------

These instructions assume that you have installed the [Heroku
Toolbelt](https://toolbelt.heroku.com/) and logged in with it.

To deploy an app using this buildpack, do the following:

1. Create a Git repository.
2. Put functioning ui.R and server.R files in your repository, like those in
   the [Shiny Tutorial](http://rstudio.github.io/shiny/tutorial/#hello-shiny).
3. Optionally, add a packages.R file to install more R packages at build
   time.  ([Here's an example](https://github.com/btubbs/shiny-example-1/blob/master/packages.R).)
4. [Create](https://devcenter.heroku.com/articles/creating-apps) your app on Heroku.
5. Enable [Heroku websockets support](https://blog.heroku.com/archives/2013/10/8/websockets-public-beta).
6. Tell Heroku to use this custom buildpack for your app:

        heroku config:set BUILDPACK_URL=https://github.com/btubbs/heroku-buildpack-shiny.git

7. Type this:

        git push heroku


Notes
-----

This buildpack does not use
[shiny-server](https://github.com/rstudio/shiny-server). That might change in
the future if just running plain old Shiny turns out to be problematic.

The version of R installed by this buildpack is 3.0.2.

The real heavy lifting of getting R to build on Heroku was done by Chris
Stefano (aka [virtualstaticvoid](https://github.com/virtualstaticvoid)) in his
[buildpack for R](https://github.com/virtualstaticvoid/heroku-buildpack-r).
Thanks Chris!
