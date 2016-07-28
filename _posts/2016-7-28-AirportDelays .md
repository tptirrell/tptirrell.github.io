---
layout: post
title: What Causes Airport Delays?
---

**Objective**: To analyze airport data to understand the cause of airport delays using Principal Component Analysis.

The first step was to load the airport data from three .csv files that included airport information, cancellation counts, and delay details.
After merging the data to one data frame and dropping any rows with missing airport info, 799 rows remain. I selected a few key features and
ran a pairplot to see any initial correlations.


![functions](/images/airport/pairplot.png)


The below graph shows the mean on-time gate arrival percent for each FAA region from 2004-2014. Most FAA regions remain pretty constant with ANM 
consistently the highest on-time percent. AEA remained at the lowest on-time percent for this period. AAL is the only region to show an 
improvement -- and a dramatic one at that. In 2004, this region's OT% was 0.65 (with the next lowest at 0.73), and in 2014 increased their OT% 
to the highest of all regions to 0.86 (with the second best at 0.81).
![functions](/images/airport/graph1.png)


The below graph simply shows FAA region by size (number of departures). It's important to note that the largest region, ANM, had the consistently 
highest OT% over the 10 year span.
![functions](/images/airport/graph2.png)


Before getting to Principal Component Analysis, I ran the clustering methods on the data as-is to get a baseline.

**K-Means Clustering**
After scaling the data using the StandardScarler in sklearn, I ran a k-means clustering and measure with a silhouette score. We need 
to determine the number of clusters,k, so we can fit the model a few times until we find the maxinum silhouette score which happens to be 0.292
with a k value equal to 5. Code below:

![functions](/images/airport/kmeans1.png)

**Hierarchical Clustering**
The second clustering method I chose was Hierarhical which I ran with the code below. The cophenetic correlation coefficient, c, compares the pairwise
distances to those implied by the hierarchical clustering. The c, in this case, is 0.782 with a maximum value of 1. The silhouette score was also calculated to 
be: 0.539. Code below:

![functions](/images/airport/hier.png)

The resultant dendrogram is below:

![functions](/images/airport/dendrogram1.png)

**PCA**
The next step is PCA. First, I found the covariance matrix and with that was able to find EigenValues and EigenVectors. The explained variance
was then calculated by divided each EigenValue by the sum of all the EigenValues. By sorting and finding the cumulative sum, you can verify the 
variance explained by the number of components. In this case, using three principal components, 86% of the variance is explained. The new components
were then plotted on a 3D plot.

![functions](/images/airport/3d.png)

To see the effects of PCA, I ran the K-Means and Hierarchical clustering again with the new principal components. 
The silhouette scores were 0.315 and 0.566, respectively which shows an improvement. Below is the dendrogram post PCA.

![functions](/images/airport/dendrogram2.png)

**Logistic Regression**
Finally, I ran a logistic regression to be able to determine which features are most correlated with delays. I created a binary feature if the avg gate arrival delay was 
less than or greater than the median delay. After running the logistic regression, the features most correlated with delays are: Avg Block Delay, Airport Departure Delay, Block Delay, and Gate Depart Delay.

![functions](/images/airport/logfeatures.png)

**Recommendations**
1 - Take a closer look at the AAL region to determine what additional conditions were present that caused the dramatic increase in on-time percentage.
2 - ANM, for being the region with the most departures, had the highest consistent OT%. What conditions were present here to maintain that rate?
3 - According to the logistic regression, block delay is the single largest contributor to gate arrival delays. How can we decrease this moving forward?




