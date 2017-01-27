---
title: Introduction
sidebar: mydoc_sidebar
permalink: mydoc_introduction.html
folder: mydoc
---

## Definitions

**Feature Vector**: Vector representing numerical representaitons of features of input set

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$$ \vec{x} = [x_1, x_2, ..., x_d]^T$$

**Binary Labeling**: Set of possible "labels" for data. (e.g. male - female)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$$ y \in \{-1, 1\} $$

**Training Set**: Set of feature vectors with accompanying labels to use to train model

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$$ S_n $$

**Classifier**: Model used to predict appropriate labels for given feature vectors

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$$ h: \mathbb{R} \rightarrow y$$

## Introduction to Supervised Machine Learning

Our goal is to learn a mapping from an input vector $$ \vec{x} $$ to an output $$ y $$ by using a training set of input-output pairs $$ \{(\vec{x}_i, y_i)\}_{i=1}^n $$.

Our input is a vector of _features_ such as height and weight of a person or timing of a heartbeat. The output can be either categorical or nominal from some finite set. An example of a binary categorical output is male or female, while an example of a nominal output is predicted age. If $$ y_i $$ is categorical, the problem is classification or pattern recognition, while if $$ y_i $$ is nominal, the problem is regression.

Our goal is to select the best possible classifier $$ h \in H $$ that would have the best chance of correctly classifying new examples. We use a _learning algorithm_ to select $$ \hat{h} $$ from $$ H $$. This learning algorithm is typically an optimization problem with respect to our training set $$ S_n $$.

**Generalization**: How well the classifier works on future examples. A training set that performs much better on training data than future data is said to have "poor generalization".

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This is an example of a classifier $$ \hat{h} $$ which earns 100% accuracy on the training set, but is unlikely to perform well on future data. This is maximum overfitting.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
$$
\hat{h}(\vec{x}) =
\begin{cases}
y^{(t)}, \quad \text{if} \  \vec{x}^{(t)} = \vec{x} \\
-1, \quad \text{otherwise}
\end{cases}
$$

So, as you may have hypothesized, there are a _lot_ of choices in $$ H $$. So, we must find a way to constrain $$ H $$. Finding the right set $$ H $$ is a key problem in machine learning. This is called model selection. It describes the choice of type of model, so that the machine learning algorithm can find the optimal model for the given training set.

## Training Error

* By convention, we consider points that lie on the decision boundary as incorrectly classified

Training error can be defined as the fraction of training examples for which the classifier with parameter $$ \vec{\theta} $$ predicts the wrong label.

$$ E_n(\vec{\theta}) = \frac{1}{n} \sum_{i=1}^{n}[[y^{(i)} \neq h(\vec{x}^{(i)}, \vec{\theta})]] $$

which is equivalent to

$$ E_n(\vec{\theta}) = \frac{1}{n} \sum_{i=1}^{n}[[y^{(i)}(\vec{\theta} \cdot \vec{x}^{(i)}) \leq 0]] $$


{% include links.html %}
