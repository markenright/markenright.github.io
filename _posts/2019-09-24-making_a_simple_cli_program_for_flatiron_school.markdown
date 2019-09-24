---
layout: post
title:      "Making a simple CLI program for Flatiron School"
date:       2019-09-24 18:21:25 +0000
permalink:  making_a_simple_cli_program_for_flatiron_school
---


After finishing the Object Orientation section of the Flatiron Software Engineering course, it's time to build your first project!  

Reaching this point gave me mixed feelings, to say the least.  I was excited to build something on my own, but worried about 1) divining a good project to make and 2) being able to make it.  I felt pretty good about the course and using Ruby at this point.  The area I still felt the most at sea with was web scraping.  And wouldn't you know it, the project would feature that extensively.

## Step 1: CLIProject::Idea.create

Oh if only it was that easy.  I guess it would be, if someone out there would make a gem for this.  Maybe someday.  Alas I had to do it the old-fashioned way.  Initially I wanted to follow one of the suggestions given in the project page - to scrape data about local libraries.  And I started to do just that.  But here I confirmed my notion that my web scraping needed more practice, and I couldn't find a perfect way to extract the data I wanted.  I think the site I was using as a source was overly complicated and perhaps had javascript loading, but regardless I decided to move on.

And it was just as well I did because I liked my next project idea even more.  I'm a fan of soccer(football) and follow the English Premier League.  It seemed natural then to make a CLI for it.  I thought it would be cool to be able to see the current standings of the league (which they call the *Table*, not to be confused with an HTML table) right from the terminal.  So that's what I did. 


## Step 2: CLIProject::Code.write

So where to start?  For me, it was easiest to start at the ending.  My ultimate goal was to have a class create an object of the current EPL teams and their stats.  From there I worked back to the source of my data (the web) and then accessed both with a CLI class.  The CLI class would run at the start of the program and also do the input prompting to the user.

```
attr_accessor :position, :name, :games_played, :won, :drawn, :points
```
What I love most about code, and particularly Object Oriented Programming, so far is seeing real world stuff implemented and abstracted as bits of code.  A club object with these attributes makes it incredibly obvious what the code is doing.  

And here is a little more about how I created those objects:

```
def initialize(position = nil, name = nil, games_played = nil, won = nil, drawn = nil, points = nil )
        @position = position
        @name = name
        @games_played = games_played
        @won = won
        @drawn = drawn
        @points = @won.to_i*3 + @drawn.to_i*1
        @@all << self
    end

    def self.table_builder(data_array)
        data_array.each do |index|
            self.new(index[0], index[1], index[2][0], index[2][1], index[2][2])
        end
    end 
```
In this code, data_array is the result of my scraping from ESPN's EPL page.  I iterate over it, creating a new club object each time by pulling particular parts of the data out.  This creates 20 objects (for all 20 teams in the league).  My CLI class then displays the full table.  It then asks the user if he or she would like to see additional info about a team.  A number from 1-20 can be selected and the program will display the rest of the info for that team. 


## Final Thoughts

This was a fun first project and I'm looking forward to doing more.  I definitely need practice in creating programs "from scratch".  Using Flatiron's testing and submit process is helpful, but doing everything yourself from the ground up is a different experience.  

I need further practice with web scraping and HTML/CSS, which go hand in hand.  I'm not sure how much more we will use it in this course but I need to learn it anyway. 

Thank you for reading!

