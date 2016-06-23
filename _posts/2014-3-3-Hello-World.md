---
layout: post
title: You're up and running!
---


Upon looking at Billboard data in the year 2000, the first thing I wanted to know was how the top songs for the year are determined. 

Before we can get to that though, I had to clean some of the data to a usable form -- namely turning the date into pd.datetime standard and turning the weeks in 
which the song was not on the chart into np.nan so these data can be understood.

Turns out, a scoring system
is used where a song is given a set number of points based on its rank for each week that it is on the chart. 100 points is given to the top song of the week and
1 point to the 100th song. Knowing this, I found the top 25 songs of the year by adding a new columns to the data frame (number of weeks on chart) and calculating
each song's score. 

***And the winner is.... Faith Hill with Breathe.***
 
***pic of faith hill***

Here is a list of the top 25 songs of the year. 

***pic of top25***

The next thing that I wanted to know was what factors contribute most to a song's score. Below you can see scatter plots score against:

1. 	Position the first week it entered the chart
2. 	The number of weeks it took for the song to peak
3. 	The percentage of time the track spent climbing to its peak relative to overall time spent on the chart
4. 	Final chart position
5. 	Weeks spent on chart
6. 	Week of calendar year that the song entered the chart

***pic of graphs 1-6***

***The interesting takeaways from each chart are:***

1. 	The songs that charted higher on their first week are not significantly more likely to reach a higher score.
2. 	The songs that reached top scores did not peak until their 30th week on the charts as opposed to hitting top 10 early and staying there.
3. 	The highest scoring songs peaked 50-80% of the way through their time on the charts.
4. 	Very Interesting - There is a clear cut off around 1000 points for songs with chart position worse than 50. I'll talk about why later.
5. 	This chart makes sense. The longer a song is on the chart, the more points it will earn.
6. 	The is no clear relationship between score and the time of year that a song debuted. It may be worth noting that 6 of the 8 songs that 
	3000 points debuted in the first half of the year. This may be coincidental given the small sample size.


Now, since weeks on chart is a major factor in a song's score, Let's see if there is any relationship between the number of weeks spent on chart
and these variables:

1.	The number of weeks it took for the song to peak
2.	Final chart position
3.	Position the first week it entered the chart
4.	Week of calendar year that the song entered the chart

***pic of graphs 1-4***


***The interesting takeaways from these charts are:***

1. The longer that a song takes to peak, the longer it will be on the chart. 
2. Just about every song either spends less than 20 weeks and falls off the chart from a position between 80-100 or spend more than 20 weeks and end at a position between 30-50.
3. There is no real relationship between number of weeks on chart and the position at which a song enters the charts. As seen on chart two, it is worth noting that there is a collection of songs that ended after 20 weeks on the chart.
4. There is no real relationship between number of weeks on chart and the week in the calendar year in which it entered the charts. The same concentration of songs that ended on 20 weeks can be seen here as well.


After researching this, it turns out that Billboard had a policy at that time to drop a song from the chart if it had already charted for 20 weeks and fell below position 50. This explains the high number of songs on the chart for exactly 50 weeks seen in graphs 3 and 4 and also the only songs with weeks longer than 20 had higher chart positions seen in graph 2.

Graph 4 in the first section shows a clear divide between songs finishing their chart run between positions 80-100 and songs ending between positions 30-50. This happens around 1000 points, and this now makes sense given the 20 week and rank 50 threshold.


Problem Statement


