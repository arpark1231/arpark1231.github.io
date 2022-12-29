---
layout: post
title: "Overfitting vs. Underfitting"
subtitle: "Model Validation"
background: '/img/posts/training_testing_validation/ML1.jpg'
---

# Model Validation: Overfitting and Underfitting 

In the previous post, we've learned K-fold cross validation method for splitting the whole dataset in terms of model selection.

If you are not sure about this topic,  
check here: [K-fold Cross Validation for model selection in ML](https://arpark1231.github.io/2022/12/27/Cross_Validation.html)

In this post, we will learn:
1. Two most common problems of models by model validation: **<mark style="background-color: lightblue">Overfitting</mark>** and **<mark style="background-color: lightblue">Underfitting</mark>**
2. What a good model actually is.

When validating a model, we check how well the model will predict for an unseen data in the future.

A poor model can show either overfitting or underfitting when validating the model performance during training.  

The model with overfitting or underfitting has no power of generalization, which means that it cannot predict well for an unseen data.

**<mark style="background-color: lightblue">Overfitting</mark>** means that the model is **too fit** to the training dataset.  
The overfitted model cannot work well on a new dataset since it is tailored to the specific training dataset.  
It is like the model **did not learn** the patterns of the training data set, but just **memorized** all the details of the training dataset including its noises.

![png](/img/posts/overfitting_underfitting/Overfitting_new.png){:width="250"}

**<mark style="background-color: lightblue">Underfitting</mark>** means that the model is even **not fit** to the training dataset.   
The underfitted model cannot work well on a new dataset since it is not even work well on the training dataset.  
One possible cause is that the model **could not learn enough** because of insufficient training dataset.

![png](/img/posts/overfitting_underfitting/Underfitting_new.png){:width="250"}

What we need to do is find **a good model** that shows **an optimal fitting** between underfitting and overfitting.

![png](/img/posts/overfitting_underfitting/Optimal_Fitting.png){:width="250"}

For the **optimal fitting** of a good model, we need to know the concept of the **bias-variance trade-off**.

Here is the quick overview regarding the concept.

* Overfitting: A model with low bias and high variance
* Underfitting: A model with high bias and low variance
* Optimal Fitting: A model with low bias and low variance

In the next post, we will learn:
1. What is **<mark style="background-color: lightpink">Bias</mark>** and **<mark style="background-color: lightpink">Variance</mark>**
2. What is **<mark style="background-color: lightpink">Bias-Variance Trade-Off</mark>**


<br/>
#### References

* Reference1: [Overfitting and Methods of Addressing it](https://analystprep.com/study-notes/cfa-level-2/quantitative-method/overfitting-methods-addressing/)
* Reference2: [Model Validation: Problem Areas and Solutions – Overfitting and Underfitting](https://rocketloop.de/en/blog/model-validation-overfitting-underfitting/) 
* Reference3: [What is Overfitting in Computer Vision? How to Detect and Avoid it](https://viso.ai/computer-vision/what-is-overfitting/)
* Reference4: [What is underfitting and overfitting in machine learning and how to deal with it.](https://medium.com/greyatom/what-is-underfitting-and-overfitting-in-machine-learning-and-how-to-deal-with-it-6803a989c76)
* Reference5: [Overfitting and Underfitting With Machine Learning Algorithms](https://machinelearningmastery.com/overfitting-and-underfitting-with-machine-learning-algorithms/)
* Reference6: [Overfitting and underfitting in machine learning](https://www.superannotate.com/blog/overfitting-and-underfitting-in-machine-learning)
* Reference7: [Epoch vs Batch Size vs Iterations](https://towardsdatascience.com/epoch-vs-iterations-vs-batch-size-4dfb9c7ce9c9)
