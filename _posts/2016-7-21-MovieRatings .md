***What makes a good movie?***

Objective: To review and analyze data from the best and worst movie lists and build a model that will predict the IMDb score of a movie.

First thing that we want to do is obtain a set of good and bad movies. I chose the NYTimes list of best 1000 ever made (http://www.nytimes.com/ref/movies/1000best.html) and 
Wikipedia's list of worst movies (https://en.wikipedia.org/wiki/List_of_films_considered_the_worst). These lists are scraped using Beautiful Soup.

[code]

The next step is to download as much information about each movie as possible. For this, I used OMDb API and loaded to a dataframe.

[code]?


After cleaning up the data, we can now take a closer look. Below are graphs of best movies and worst movies by country. (Note: If there were multiple
countries listed for a movie, the first was used.)

[best and worst movies by country]

[english/not english]




![functions](/images/Titanic/survivalper.png/)
![functions](/images/Titanic/percentagetable.png/)

Before we run a logistic regression, we'll need to choose the features. I broke out class by gender so that our features are child, first class male, 
first class female, second class male, etc.

The coefficients of the regression are listed below, and you can see the likelihood of survival increases with class and decreases for males over females.

![functions](/images/Titanic/coefs.png/)
![functions](/images/Titanic/coefstable.png/)

The cross val score for this model is 0.7896, and the confusion matrix is below:

![functions](/images/Titanic/cm1.png/)

The confusion matrix tells us that the model is very accurately predicting survivors (precision score = 88%) but is also predicting many as survived that actually were deceased (recall score = 54%). In other words, we're predicting almost all survivors accurately at the expense of also predicting almost half of the deceased as also survivors.

The ROC curve for this model looks like this:

![functions](/images/Titanic/roc1.png/)

The ROC curve is the relationship between False positives and True Positives. As the model accuracy improves by accuraretely prediciting more true positives, the false positives also increase. This ROC curve shows a very strong model.


We then run Gridsearch with logistic regression to find the best parameters, and they are as follows:

![functions](/images/Titanic/params1.png/)

We can also compare Gridsearch with kNN to see how these best parameters compare, and we see that the score is slightly higher with kNN.:

![functions](/images/Titanic/param2.png/)

We can then rerun our model with these paramaters and compare the confusion matrix and ROC curve.

![functions](/images/Titanic/cm2.png/)
![functions](/images/Titanic/roc2.png/)

The accuracy of this model is just slightly higher with a score of 0.8000 as compared to 0.7966 with the first model.


