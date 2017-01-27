---
title: Linear Classification
tags:
  - classification
keywords: "features, capabilities, scalability, multichannel output, dita, hats, comparison, benefits"
last_updated: "January 20, 2017"
summary: "An introduction to linear classification, the most basic type of classification"
published: true
sidebar: mydoc_sidebar
permalink: mydoc_linear_classification.html
folder: mydoc
---

## Introduction to Linear Classification

**Hyperplane**: A linear surface with $$ (d-1) $$ dimensions in a $$d$$-dimensional space

**Training Error**: Fraction of training examples for which the classifier with parameter $$ \theta $$ predicts the wrong label

The goal of classification is to take an input vector $$ \vec{x} $$ and assign it to one of $$ K $$ discrete classes $$ C_k $$ where $$ k = 1,...,K $$. In simpler scenarios, the classes can be considered disjoint, so that each input is classified into exactly one class $$ C_k $$.

Mapping input vectors to labels is be done by dividing the input space into _decision regions_. These regions are bounded by _decision boundaries_ which mark the separation between classification classes.

In linear classifications, the decision boundaries are strictly linear functions of the input vector $$ \vec{x} $$. In 2-dimensional models these are simply lines, but this can be generalized into higher dimensions with $$ (d-1) $$-dimensional hyperplanes within the D-dimensional input space.

In a classification with disjoint classes, our target space can be represented as a vector of length $$ k $$ (the number of possible classes), with all zeroes, but one $$ 1 $$. As an example, a possible classification of an input vector into a 3-dimensional target space could be: $$ \vec{t} = [0, 1, 0]^T $$, where we have classified the input into class 2.

In simple binary classification, an incorrect prediction occurs when $$ y^{(i)} $$ does not have the same sign as $$ \vec{\theta} \cdot \vec{x} $$. Unfortunately, a reasonable algorithm for finding $$ \vec{\theta} $$ that minimizes training error is not easy to solve in general.

#### Special Case: Linearly Separable

If training examples $$ S_n $$ are linearly separable, meaning there exists such a vector $$ \vec{\theta} $$ such that $$ y^{(i)} (\vec{ \theta } \cdot \vec{x}^{(i)}) > 0 $$ $$ \forall_i=1,...,n $$

## Perceptron Algorithm

The perceptron algorithm is a mistake driven algorithm for linearly separable data. Intuitively, when we misclassify a point, we simply adjust our parameter $$ \vec{\theta} $$ by a certain amount. The Perceptron algorithm for a linear classifier passing through the origin is defined below:

k = 0 \\
$$ \vec{\theta}^{(k)} = \vec{0} $$ \\

while not all points are correctly classified: \\
  for i in 0...n: \\
    if $$ y^{(i)} \neq h(\vec{x}^{(i)}; \vec{\theta}^{(k)} $$: \\
      $$ \vec{\theta}^{(k+1)} = \vec{\theta}^{(k)} + y^{(i)} \vec{x}^{(i)} $$ \\
      k++ \\


It is important to note that after an update, it is not guaranteed a previously misclassified point will be correctly classified the next iteration. If the misclassified point is small in magnitude, the perceptron could only adjust my a small amount, too small to reclassify the example. However, after multiple iterations, the algorithm will eventually correctly classify the example The perceptron algorithm is guaranteed to converge after a finite number of mistakes when the training examples are linearly separable.

To accomodate for a linear classifier not going through the origin, the algorithm could either be updated to include an offset parameter, or $$ \vec{\theta} $$ and $$ \vec{x} $$ could be adjusted to $$ \vec{\theta} = [b, \vec{\theta}], \vec{x} = [1, \vec{x}] $$. This evaluates to $$ \vec{\theta} \cdot \vec{x} = b + \vec{\theta} \cdot \vec{x} $$.

## Loss Functions

A loss function, also called a cost function, maps vectors into a real number representing an associated cost of having the vector. We typically want to optimize the loss function by minimizing it, or, if the values are negative (reward function), it should be maximized in the optimization.

## Stochastic Gradient Descent

Stochastic gradient descent (SGD) tries to optimize with iteration by using a stochastic approximation to minimize a loss function. Intuitively, SGD iteratively adjusts parameters toward a minimum (ideally global) in the loss function.

An important factor in SGD is the step size. The step size sets how far the parameters $$ \vec{\theta} $$ adjust per iteration. The value of the step size is called the _learning rate_. Simple methods may set the learning rate as a static value. However, more complex methods utilize a learning rate schedule. As you may assume, as you move closer to the minimum, leaving the step size static could cause you to overshoot the minimum. Common formulas for the learning rate schedule are $$ \eta_k = \frac{1}{k} $$ or $$ \eta_k = (\tau + k)^{-\kappa} $$ where $$ \tau \geq 0 $$ slows down early iterations, and $$ \kappa \in (0.5, 1] $$ controls rate that old values are forgotten. Adjusting these parameters can prove difficult and thus it is common to try a range of $$ \eta $$ values and choose the one that results in the fastest optimization of the loss function.

  As SGD involves a step size and iteration, it is possible to have a non-converging model. It is thus common to implement *early stopping* as terminating when the adjustment to $$ \vec{\theta} $$ reaches some small threshold.



## Probabilistic Classification
Page 180

## Discriminant Functions

**Discriminant**: function that takes input vector $$ \vec{x} $$ and assigns it into $$ C_k $$. 

We can represent a binary classifying linear discriminant as $$ y(\vec{x}) = \vec{\theta}^T\vec{x} + b $$ where $$ \vec{\theta} $$ is a weight vector and $$ b $$ is a bias. An input vector $$ \vec{x} $$ is assigned to class $$ C_1 $$ if $$y(\vec{x}) > 0 $$ and $$ C_2 $$ otherwise.

{% include links.html %}
