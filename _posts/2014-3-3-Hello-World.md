---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

Here is some basic text
![_config.yml]({{ site.baseurl }}/images/config.png)

Introduce Billboard Scoring
Upon looking at Billboard data in the year 2000, the first thing I wanted to know was how the top songs for the year are determined. 

Before we can get to that though, I had to clean some of the data to a usable form -- namely turning the date into pd.datetime standard and turning the weeks in 
which the song was not on the chart into np.nan so it could be understood as such.

Turns out, a scoring system
is used where a song is given a set number of points based on its rank for each week that it is on the chart. 100 points is given to the top song of the week and
1 point to the 100th song. Knowing this, we can calculate the score for each song and see the top 25 songs of the year.

And the winner is.... Faith Hill with Breathe.






Top 25 Songs
What Impacts Track Score
What Impacts Chart Length
Problem Statement and Support
