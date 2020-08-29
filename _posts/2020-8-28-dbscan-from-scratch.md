---
layout: post
title: DBSCAN from Scratch
cover: cover.jpg
date:   2020-08-28 17:40:00
categories: posts
---



# DBSCAN from Scratch

## The Sales Pitch

Data scientists *love* labeled data, and *hate* labeling data. It's time-intensive and not 
so brain-intensive, and what's more can get pretty expensive if you want to pawn the job
off onto someone else. Thankfully, a number of algorithms exist for doing cluster analysis - 
automatically assigning the elements of a data set to groups, generally based upon some 
notion of distance, density, or connectedness. Among their many other uses, these algorithms 
can be used to make a first pass over an as-of-yet unlabeled dataset to hasten a manual labeling job, or simply as a kind of exploratory data analysis of their own; a way of revealing the internal structure of a dataset, perhaps without the prejudices that a manual assignment of labels might pass on.

DBSCAN (Density-based spatial clustering of applications with noise) is a particularly popular clustering algorithm, and probably the most popular of the density-based subset. The method by which it assigns points to clusters is relatively intuitive and interpretable, and whats more it also can make distinctions between clusters which are *not linearly separable*. That is to say, if the groups in your data are not something like multiple "blobs", but rather something like a central "blob" surrounded by a "ring", DBSCAN can properly draw the distinction between the central blob and the ring, whereas other algorithms like K-means will not. On the other hand, pre-specifying some expected number of groups is not possible with DBSCAN, unlike K-means. If you need to be able to specify a pre-existing number of clusters (maybe due to some domain knowledge that you have) DBSCAN might not be the best choice - but if that doesn't apply, give it a go!

## The Spec

DBSCAN asks for three main parameters to cluster data - a value maximum_radius, often written ε, which will define a region around a point; a value minimum_points, which will decide how we classify points (as a member of a cluster or as noise), and finally a distance metric to define how far apart points are.

DBSCAN categorizes points as core points, border points, and noise points. Both core and border points are members of clusters; noise points are not. A point is a core point if the number of points within the defined maximum radius of it is greater than or equal to the defined minimum number of points - these points will form the core of a given cluster. Two points are *directly reachable* from one another if they are within each other's maximum radius. Two points are *reachable* if there is some path of directly reachable points that you can take between the two points. Points are border points if they are *reachable* from some core point; they'll make out the boundary of a given cluster. Finally, noise points are not reachable from any other point in the set.


So DBSCAN will do the following: 
- It will look at each point in the dataset.
- If the point it is looking at has not yet been labeled, it will examine the set of remaining points, and find those which fall within maximum_radius of the original point.
- It will count those points that fell within maximum radius. If the number is less than minimum_points, it will label the point *noise*.
- If the label is greater than minimum points, it will label the point a core point with a new cluster id *c*. It will then examine the neighbors of this new core point. If the point had been previously labeled noise, it will assign the point the label *c*. 
- If the point had not yet been labeled, it will assign the point the label *c*, and examine its neighbors. For each of those neighbors, it will repeat the above process of checking the current label - relabeling as *c* if it had been labeled noise, and relabeling as *c* and checking neighbors if it had been unlabeled.
- Finally, any point already labeled with a cluster label will be left as it was.
- Once this process has been performed for each point in the dataset, clustering is complete!

I broke this out into three main methods - a get_neighborhood() method which returns all the points in the point set within a given radius of a certain point, a broad fit() method which carries out the outer loop over all points in the set, and a recursive expand_cluster() method which carries out the inner loop of finding the neighbors of neighbors and assigning them labels until noise and/or the borders of other clusters are reached.

*You can find my implementation [here](https://github.com/crsanderford/CS-Data-Science-Build-Week-1).*