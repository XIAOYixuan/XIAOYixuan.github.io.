---
title: "416 Review&Random notes"
tags: [Pattern Recognition & Machine Learning, Random Notes]
---

### Finding a ML algorithm to solve a practical problem:
> "Find a recent paper at a top machine learning conference, like NIPS or ICML  that's on the sort of task you need to solve. Look at the baseline that they compare their method to ... and implement that."

### If a paper reports a K-fold score in place of a test set error
 Iain said it would take $$K^2$$ experiments to build a model to compare to the original one. In each trail, he had a small training set and a tiny test set, then to fit the hyper-parameters, let's say the regularization parameters, he couldn't set these on the test set(it would be cheating), therefore he had to run K-fold cross validation on the small training set.

### the difference between $$N(0,1)$$ and $$N(x;0,1)$$
The first one refers to distribution, the second one refers to PDF, which is a function rather than a distribution. Iain also mentioned that PDF is one possible description of that distribution.

### Why sometimes error bars(on a mean) do not reliably indicate the average of locations in future data.
We assume the distribution has a finite mean $$\mu$$ and variance $$\sigma^2$$, then let $$\bar{x}$$ be the mean estimator. 

If the data points are positively correlated(nearby points tend to be similar), the variance of the estimator(the true variance) will be larger than estimated(the one we calculated), then the error bars equal to $$\sqrt{\sigma^2/N}$$ are too small and unreliabe.
 
+ A good example, if the samples are not independant, the difference between the mean of samples and  the mean of partial training data will be much larger than the estimated standard errors. 

+ There is another related question in Assignment 2.