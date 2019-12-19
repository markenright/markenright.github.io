---
layout: post
title:      "Portfolio Project #2 - Sinatra App"
date:       2019-12-19 16:17:14 +0000
permalink:  portfolio_project_2_-_sinatra_app
---


The second project here at Flatiron school is intimidating at first.   It asks the student to write a functional web app based app that has CRUD capability.  CRUD programs are some of the most common type of program written because they are so useful.  They allow the user to Create, Read, Update, and Delete data.  

Our task was to allow a user to login, create data on the server, and then allow the user to edit that data as they saw fit (as long as it was their own).  This meant that we had to utlize the session/cookie features of Sinatra, which I will explain in brief. 

To begin using sessions in Sinatra, start in your Application Controller.  

```
enable :sessions
set :session_secret, "secret"
```

Once you enable sessions, you can access the session hash in your controllers, which will be unique to the logged in user and allow you to persist that data you need for that user until logoff.  


Another thing to note in Sinatra is how to set up your table relationships.  A "has many" relation is required for the project, and useful for most databases as well.  Here, since Sinatra can utilize ActiveRecord and it's incredible wrapping of sql and database structure, we can simply add our tables into the program's file structure as classes. 

```
class User < ActiveRecord::Base   
   
    has_many :teams
end
```

This simple statement will link the two tables, users and teams, with teams having a "foreign key" that links it to users.  The team "belongs to" a user.  

