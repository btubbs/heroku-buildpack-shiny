Heroku Buildpack Shiny
===========================

This is a Heroku buildpack for the [Shiny](http://www.rstudio.com/shiny/) web
framework that runs on [R](http://www.r-project.org/).

Check it out: http://shiny-example-1.herokuapp.com/

Instructions
------------

These instructions assume that you have installed the Heroku Toolbelt and
logged in with it.

To deploy an app using this buildpack, do the following:

1. Create a Git repository.
2. Put functioning ui.R and server.R files in your repository, like those in
   the [Shiny Tutorial](http://rstudio.github.io/shiny/tutorial/#hello-shiny).
3. Optionally, add a packages.R file to install more R packages at build
   time.  ([Here's an example](https://github.com/btubbs/shiny-example-1/blob/master/packages.R).)
4. [Create](https://devcenter.heroku.com/articles/creating-apps) your app on Heroku.
5. Enable [Heroku websockets support](https://blog.heroku.com/archives/2013/10/8/websockets-public-beta).
6. Type this:

  git push heroku

This buildpack does not use
[shiny-server](https://github.com/rstudio/shiny-server). That might change in
the future if just running plain old Shiny turns out to be problematic.
