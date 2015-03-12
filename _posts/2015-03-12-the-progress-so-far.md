---
layout: post
title:  "The progress so far"
date:   2015-03-12 22:12:23
categories:
---

Hey everyone!

Sorry for the delay.
We have been quite busy but we won't keep you waiting much longer.
*Read on!*

## Classification

The last few weeks we have been going through articles and websites learning about different classification methods namely:

#### 1. Naive  Bayes Classification

The Naive Bayesian classifier is based on Bayes theorem with independence assumptions between predictors.
A Naive Bayesian model is easy to build, with no complicated iterative parameter estimation which makes it particularly useful for very large datasets.
Despite its simplicity, the Naive Bayesian classifier often does surprisingly well and is widely used because it often outperforms more sophisticated classification methods.

Naive Bayes is a simple technique for constructing classifiers which are models that assign class labels to problem instances.
This is not a single algorithm, but a family of algorithms based on a common principle.

This method categorizes the documents or information based on the word frequencies as the features.
There is an assumption that the value of a particular feature is independant to the value of any other feature.

For example, a fruit may be considered to be an apple if it is red, round, and about 3" in diameter.
A Naive Bayes classifier considers each of these features to contribute independently to the probability that this fruit is an apple, regardless of any correlations between the color, roundness and diameter features.

#### 2. Maximum Entropy Classification

The Maximum Entropy classifier is a probabilistic classifier which belongs to the class of exponential models.
Unlike the Naive Bayes classifier that we discussed before, the Maximum Entropy does not assume that the features are conditionally independent of each other.
The Maximum Entropy classifier is based on the Principle of Maximumimum Entropy and from all the models that fit our training data, selects the one which has the largest entropy.
The Maximum Entropy classifier can be used to solve a large variety of text classification problems such as language detection, topic classification, sentiment analysis and more.

The underlying principle of maximum entropy is that without external knowledge, one should prefer distributions that are uniform.
The constraints on the distribution, which we get from labeled training data, helps the technique understand where to be minimally non-uniform.
The maximum entropy formulation has a unique solution which can be found by the improved iterative scaling algorithm.

This technique provides the least biased estimate possible based on the given information.
In other words, "it is maximally noncommittal with regards to missing information".

#### 3. Support Vector Machines

A Support Vector Machine (SVM) is a discriminative classifier formally defined by a separating hyperplane.
In other words, given a labeled training data (supervised learning), the algorithm outputs an optimal hyperplane which categorizes new examples.

This algorithm analyzes data and recognises patterns which helps in classification and regression analysis.
Given a set of training examples, each marked as belonging to one of two categories, an SVM training algorithm builds a model that assigns new examples into one category or the other.

An SVM model is a representation of the examples as points in space, mapped so that the examples of the separate categories are divided by a clear gap that is as wide as possible.
New examples are then mapped into that same space and predicted to belong to a category based on which side of the gap they fall on.

We have been reading different research papers and trying to understand how they have implemented the classification, and it shows us new ideas that they are using, like unigram models, tree kernel models, multi-feature models and more!

## Cleaning up of Tweets

On the other hand, seeing as we have obtained the tweets, we have started cleaning it up so that it can be processed properly, using regular expressions, we clear up the unwanted mess that a tweet sometimes can be.

The steps are:

1. change the entire case of the tweet into lower case
2. replace the `@name` mention with `"AT_USER"`
3. replace urls like `www.xyz.com` or anything starting with `http://` with `"URL"`
4. replace the `#hashtags` with `"hashtags"`, removing the `'#'` symbol
5. remove additional punctuations and whitespaces

## Web app interface

We have also started work on a web app, which will provide the interface to end users for the sentiment analysis of tweets.
There isn't much work to do on this yet but we decided to start work on this too while we decide on how to classify the tweets.

As you can see, we have been quite busy with all of this and weren't able to provide updates as often as we would like.
However, we promise to be more regular from now on.
