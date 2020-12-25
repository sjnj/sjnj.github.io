---
layout: post
title: A rotation away from understanding Ridge regression
---

In this post we will understand the ridge regression, i.e. linear regression with $$l_2$$  regularization.
This task is simplified if we change our features performing a PCA rotation into the principal components coordinate 
system.

**Notation:**
  
  * $$x \in \mathbb{R}^m =  [ x_1,...,x_m]$$ is a random variable that represents all the studied features.  $$x_i$$ corresponds to a single feature, the ith coordinate of $$x$$.

  * $$X_{n \times m}$$ is a matrix that contains the samples of our dataset.  Thus, $$X_{ij}$$ correponds to the meassured value of the jth variable for the ith sample from the population studied.



   


```

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one.
 Go into /_posts/ and update the Hello World markdown file. 
 For more instructions head over to the 
 [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
