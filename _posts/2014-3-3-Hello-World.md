---
layout: post
title: A rotation away from understanding Ridge regression
---

In this post we will understand the ridge regression, i.e. linear regression with $$l_2$$  regularization.
This task is simplified if we change our features performing a PCA rotation into the principal components coordinate 
system.

### Notation:
  
  * $$x \in \mathbb{R}^m =  [ x_1,...,x_m]$$ is a random variable that represents all the studied features.  $$x_i$$ corresponds to a single feature, the ith coordinate of $$x$$.

  * $$X_{n \times m}$$ is a matrix that contains the samples of our dataset.  Thus, $$X_{ij}$$ correponds to the meassured value of the jth variable for the ith sample from the population studied.
  

**Example:**

$$\begin{array}{|l|c|c|}
\hline
 \text{} & \textbf{Height (m)} & \textbf{Weight (kg)}\\
 \hline
\text{person 1} & 1.90 & 100.5\\
\hline
\text{person 2} & 1.67 & 67.1\\
\hline
 \text{...} & \text{...} & \text{...}  \end{array} $$



$$x_1 = \text{Height},\;\;\;x_2 = \text{Weight},\;\;\;x = [\text{Height}, \text{Weight}]$$

$$X_{12} = 100.5,\;\;\;X = [[1.90, 100.5],\;[1.67, 67.1],\;...]$$


## Understanding PCA
    

Let us assume that the variables satisfy:

* $$E[x_i] = 0;\;\; \forall i \tag{1} \label{cond1}$$

* $$Var[x_i] \equiv E[(x_i - E[x_i])^2] = E[x_i^2] = 1;\;\; \forall i  \tag{2} \label{cond2}$$

We can always find a transformation such that those conditions are approximately satisfy:

$$ x_i \longrightarrow \frac{x_i - \overline{x}_i}{\sigma_i};$$

$$\overline{x}_i  = \frac{1}{n}  \sum_{j=1}^{n} X_{ji};\;\;\;\; \sigma^2_i  = \frac{1}{n-1}  \sum_{j=1}^{n} \left(X_{ji}-\overline{x}_i \right)^2$$


The covariance matrix reads:

$$ Var[x] = E[x^t x] = \left( \begin{array}{ccc}
E[x_1^2] & E[x_1 x_2] & \cdots \\
E[x_2 x_1] & E[x_2^2] & \cdots \\
\vdots & \vdots & \ddots  \end{array} \right)_{m \times m} = \left( \begin{array}{ccc}
1 & E[x_1 x_2] & \cdots \\
E[x_2 x_1] & 1 & \cdots \\
\vdots & \vdots & \ddots  \end{array} \right)_{m \times m}$$

We can quickly gain familiarity with what the covariance matrix represent by studying extreme cases:

* $$\bf{x_2 = \pm x_1}$$ **:** Suppose that we have include a copy of the $$x_1$$ up to a sign in the dataset without
 relalising. In that case, $$E[x_2 x_1] = \pm E[x_1^2] = \pm 1$$. Notice how this maximum is fixed thanks to condition 
 (\ref{cond2}); for example, if we had the same variables in different units
  (say $$[x_1]=m$$ and $$[x_2] = km$$),  the result would be
   $$E[x_1 x_2] = 0.001 \cdot E[x_1^{\small normalized} x_2^{\small normalized}] = 0.001$$

* $$\bf{x_2 \perp x_1}$$**:** if x_2 is independent of $$x_1$$, whatever the value of $$x_2$$, $$x_1$$ will follow the
 same distribution, i.e. $$E[x_1x_2] = E[x_1\vert x2] E[x_2] = E[x_1]E[x_2] = 0$$. Notice how this minimum is set to
  zero thanks to condition (\ref{cond1}).

Thus, the off-diagonal elements give us a score of the <span style='color:red;'> linear</span> dependency between each 
pair of variables. If $$\vert E[x_2 x_1] \vert \simeq 1$$ ,they are highly correlated. On the other hand,
 if $$ E[x_2 x_1]  \simeq 0$$, they are <span style='color:red;'> linearly</span> independent.
  Notice that linearly independent does not mean indpendent, see how the varibles of Fig. 1 has 
   $$ E[x_2 x_1]  \simeq 0$$, however if $$x_1=0$$ we are pretty sure that $$\vert E[x_2\vert x_1=0] \vert = r$$.

.center[
![_config.yml]({{ site.baseurl }}/images/post_0/correlation0.jpg)
.caption[Figure 1: Example of non correlated but dependent variables.]
 ]  



Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one.
 Go into /_posts/ and update the Hello World markdown file. 
 For more instructions head over to the 
 [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
