---
title: Nifty Web Apps
---

# Deploy your app for free

[Heroku](https://www.heroku.com/) is an app hosting company that offers a free tier. Heroku manages all of the hardware and administrative aspects of hosting a web app. All we need to do is instruct Heroku how to run the web app.

Prerequisites
: Heroku requires some comfort with the command line interface and Git.

## Create a Heroku app

First, sign up for a [free Heroku account](https://signup.heroku.com/dc) and set up the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli). Then, open a terminal and run the following commands (replacing `example` as appropriate).

```sh
mkdir example
cd example
git init
heroku create example --buildpack heroku/jvm
```

The `heroku/jvm` buildpack specifies that the app will require a Java virtual machine runtime. To specify the Java version, create a new `system.properties` file with the desired version.

```
java.runtime.version=11
```

## Tell Heroku how to run your app

Create a new `PROCFILE` to tell Heroku how to run your app.

```
web: javac Server.java && java Server
```

This instructs the Heroku `web` server to execute `javac Server.java && java Server`.

## Push your app to Heroku

Commit the web app code to the Git repository.

```sh
git add .
git commit -m "Initial commit"
```

Then, push the commits to Heroku.

```sh
git push heroku master
```

If everything's working properly, your web app is now accessible on the worldwide web!
