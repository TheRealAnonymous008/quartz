# $k$-means clustering
### Procedure
* Pick $k$ starting points from a list of sample points.
* Each data point is labelled based on which of the starting points it is closest to.
* Calculate the mean location of each cluster (i.e., its clustroid) and perform another pass of re-clustering.
	* If the clusters in this pass are the same as those in the previous pass, we can stop.
### Considerations
* Vary the sample points chosen to start the algorithm. Ideally, *we want low total variance from points to their clustroid*. 
### Choosing $k$
* Vary $k$ depending on the domain knowledge or quality of clustering.
* Use the $k$ that is at the "**elbow**" of the variance-vs-$k$ plot. 
	* This is subjective and sometimes not-obvious in the plot.
* Use the **[Silhouette method](https://en.wikipedia.org/wiki/Silhouette_(clustering))** to measure how similar points tend to be to points in their clusters compared to other clusters.
	* Pick the $k$ which maximizes the silhouette score.
# DBSCAN
* Involves creating clusters starting from select **core points**-- points which have $k$ other points within distance $\varepsilon$ of them (for tunable $\varepsilon$ and $k$).
* The cluster is extended by adding all core points that are reachable (within distance $\varepsilon$) from core points already in the cluster.
* Finally, all non-core points that are distance $\varepsilon$ to a core point in the cluster are added to the cluster.
* This process is repeated until all points are added. 
* For more information on this see [the Wikipedia page](https://en.wikipedia.org/wiki/DBSCAN)
# Hierarchical
* A technique that seeks to build a hierarchy of clusters from a specified *distance metric*
* **Agglomerative Clustering** is *bottom up*--each observation starts in its own cluster and pairs of clusters are merged as one moves up the hierarchy.
* **Divisive Clustering** is *top-down*--all observations start in one cluster, and splits are performed recursively as one moves down the hierarchy.
### Calculating Distance between Clusters
For each of these, let $D(X,Y)$ denote the distance between two clusters $X,Y$, and $d(x,y)$ the distance between two data points.
* **Complete Linkage Clustering** - clusters based on the maximum distance between two elements of two clusters. 
  $$
  D(X,Y)=\max_{x\in X, y\in Y}d(x,y)
  $$
  
* **Single Linkage Clustering** - clusters based on the minimum distance between two elements of two clusters. 
  $$
  D(X,Y)=\min_{x\in X,y\in Y}d(x,y)
  $$
  
* **Unweighted Average Linkage Clustering** - clusters based on the average distance between all pairs of elements from $X,Y$. 
  $$
  D(X,Y)=\frac{1}{|X|\cdot|Y|}\sum_{x\in X}\sum_{y\in Y}d(x,y)
  $$
  
# Gaussian Mixture Models
* Assume all datapoints with a certain label are *distributed based on a Gaussian distribution* parameterized by label-specific mean $\mu_i$, covariance $\Sigma_i$ and label probability $\pi_i$.
* The goal, then, is to *maximize the probability of observing a datapoint given the label-specific Gaussian distributions*. 
	* This is done by tweaking each of the $\mu_i$, $\Sigma_i$ and $\pi_i$.
* See more [here](https://www.youtube.com/watch?v=EWd1xRkyEog)
# Links
* [DBSCAN](https://en.wikipedia.org/wiki/DBSCAN)
* [Gaussian Mixture Model](https://www.youtube.com/watch?v=EWd1xRkyEog)
* [How to Determine the Optimal k for k-means](https://medium.com/analytics-vidhya/how-to-determine-the-optimal-k-for-k-means-708505d204eb)
* [Silhouette Method](https://en.wikipedia.org/wiki/Silhouette_(clustering))
* [StatQuest: Clustering with DBSCAN, Clearly Explained](https://www.youtube.com/watch?v=RDZUdRSDOok)
* [StatQuest: K-means clustering](https://www.youtube.com/watch?v=4b5d3muPQmA)