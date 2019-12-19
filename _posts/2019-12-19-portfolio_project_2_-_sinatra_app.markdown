---
layout: post
title:      "Portfolio Project #2 - Sinatra App"
date:       2019-12-19 11:17:15 -0500
permalink:  portfolio_project_2_-_sinatra_app
---


The second project here at Flatiron school is intimidating at first.   It asks the student to write a functional web based app that has CRUD capability.  CRUD programs are some of the most common type written because they are so useful.  They allow the user to Create, Read, Update, and Delete data.  

Our task was to allow a user to login, create data on the server, and then allow that user to edit that data as they saw fit (as long as it was their own).  This meant that we had to utlize the session/cookie features of Sinatra, which I will explain in brief. 

To begin using sessions in Sinatra, start in your Application Controller, or a dedicated Session Controller.  

```
enable :sessions
set :session_secret, "secret"
```

Once you enable sessions, you can access the session hash in your controllers, which will be unique to the logged in user and allow you to persist that data you need for that user until logoff.  Sinatra here allows us a simple and clear way to access session data.  


A "has many" relationship is also required for the project, and useful for most databases as well.  Sinatra again does the heavy lifting for us, since it can utilize ActiveRecord and it's incredible wrapping of sql and database structure, thus avoiding the need of writing SQL statements directly.  We can simply add our tables into the program's file structure as classes, and specify the relationship.  Just make sure they that each has its own file.  

```
class User < ActiveRecord::Base   
   has_many :teams
end
```

```
class Team < ActiveRecord::Base
    belongs_to :user
end
```

These simple statements will link the two tables, users and teams, with teams having a "foreign key" that links it to users.  The team "belongs to" a user.  Your program now has its database structure set up.  

