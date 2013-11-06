Heroku Buildpack Shiny
===========================

This is a Heroku buildpack for the [Shiny](http://www.rstudio.com/shiny/) web
framework that runs on [R](http://www.r-project.org/).

Check it out: http://shiny-example-1.herokuapp.com/.  The source for that is at
https://github.com/btubbs/shiny-example-1.

Instructions
------------

These instructions assume that you have already signed up for an [Heroku Account](https://id.heroku.com/signup/www-home-top) and installed the [Heroku Toolbelt](https://toolbelt.heroku.com/)

#### Create App

The first step is to create the Shiny application to deploy.

1. Create a Git repository.
2. Put functioning ui.R and server.R files in your repository, like those in
   the [Shiny Tutorial](http://rstudio.github.io/shiny/tutorial/#hello-shiny).
3. Optionally, add a packages.R file to install more R packages at build
   time.  ([Here's an example](https://github.com/btubbs/shiny-example-1/blob/master/packages.R).)

If you want to quickly test things, you can directly clone my [example application](https://github.com/btubbs/shiny-example-1)

#### Deploy App

To deploy the app on Heroku using this buildpack, you need to

4. [Create](https://devcenter.heroku.com/articles/creating-apps) your app on Heroku.
5. Enable [Heroku websockets support](https://blog.heroku.com/archives/2013/10/8/websockets-public-beta).
6. Tell Heroku to use a custom buildpack for your app
7. Push application to heroku

The commands to be run from the commandline are shown below. Make sure to replace `APPNAME` with the name of your application.
        

```bash
$ heroku apps:create APPNAME
$ heroku config:set BUILDPACK_URL=https://github.com/btubbs/heroku-buildpack-shiny.git
$ heroku labs:enable websockets -a APPNAME
$ git push heroku
```


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
