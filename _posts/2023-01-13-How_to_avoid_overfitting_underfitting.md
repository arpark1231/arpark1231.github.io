---
layout: post
title: "How to avoid Overfitting & Underfiting in Machine Learning"
subtitle: "in terms of training process, model selection & feature engineering "
background: '/img/posts/training_testing_validation/ML1.jpg'
---

# How to avoid Overfitting & Underfiting in Machine Learning

In the previous post, we've learned two common problems from machine learning models, which are "Overfitting" and "Underfitting" when validating them.  

In addition, we've learned what are the relationships of the overfitted & underfitted models with the concepts of "Bias" and "Variance". 

If you are not sure about these topics,  
check here: [Overfitting and Underfitting in terms of Model Validation](https://arpark1231.github.io/2022/12/29/Overfitting_Underfitting.html) and   
check here: [Bias and Variance](https://arpark1231.github.io/2023/01/03/Bias_Variance.html)

In this post, we will learn:
1. Three solutions to avoid overfitting in terms of training process, model selection and feature engineering 
2. Two solutions to avoid underfitting in terms of training process and model selection

<br/>

The goal of selecting the machine learning model is:

* **Goal**: Finding the best model with low bias & low variance and showing an optimal fitting (neither overfitting nor underfitting)

<br/>

## How to avoid Overfitting

**An overfitted model** has low bias & high variance as below:

![png](/img/posts/bias_variance/overfitted_model.png){:width="800"}

**Possible reasons** of overfitting and their **solutions** are as follows:  

In terms of training process,

**Reason 1.** The model **memorized** all the training dataset including its **noises**. 

**Solution 1.**   
**<mark style="background-color: lightblue">Early stopping</mark>**: 
Early stopping refers to stopping the training process earlier so that the model does not learn all the details such as noises of the training dataset.

In terms of model selection,

**Reason 2.** The model is **too complex**.  

**Solution 2.**   
**<mark style="background-color: lightblue">Regularization</mark>**:
Regularization refers to a variety of techniques to make the model to be simpler.  

**L1 and L2 regularization** are one of the methods that add a penalty parameter for a regression. This topic will be dealt with in detail in a next post. 

In terms of feature engineering,

**Reason 3.** The model uses **too many ML features**.  

**Solution 3.**   
**<mark style="background-color: lightblue">Remove features</mark>**:
Removing non-essential features can help the model find the true patterns of the task.

<br/>

## How to avoid Underfitting

**An overfitted model** has high bias & low variance as below:

![png](/img/posts/bias_variance/underfitted_model.png){:width="800"}

**Possible reasons** of underfitting and their **solutions** are as follows:  


**Reason 1.** The model **could not learn enough** the patterns of the task.

**Solution 1.**   
**<mark style="background-color: lightpink">More time for training</mark>**: 
Maybe this time, too early stopping.  
Increasing the number of epochs or the duration of training can avoid the model to be underfitted.  

In terms of model selection,

**Reason 2.** The model is **too simple**.  

**Solution 2.**   
**<mark style="background-color: lightpink">A more complex model</mark>**:
We can try to replace the linear model with a higher-order polynomial model.  
It will help us solve the problem of underfitting. 

<br/>

In the next post, we will learn:
1. What is **<mark style="background-color: lightyellow">L1 and L2 Regulation</mark>** 
2. How do they make the better ML model

<br/>

#### References

* Reference1: [Overfitting and underfitting in machine learning](https://www.superannotate.com/blog/overfitting-and-underfitting-in-machine-learning)
* Reference2: [What is Overfitting in Computer Vision? How to Detect and Avoid it](https://viso.ai/computer-vision/what-is-overfitting/)
