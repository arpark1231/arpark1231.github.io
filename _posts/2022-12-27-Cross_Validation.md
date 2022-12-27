---
layout: post
title: "K-fold Cross Validation for model selection in Machine Learning"
subtitle: "What is it and why we use it"
background: '/img/posts/training_testing_validation/ML1.jpg'
---

# K-fold Cross Validation for model selection in ML

In the previous post, we've learned why we split the dataset into training, validation and testing dataset in terms of machine learning.

If you are not sure about this topic,  
check here: [Training, Testing and Validation Datasets in Machine Learning](https://arpark1231.github.io/2022/12/24/Train_Test_Validation_Datasets.html)

In this post, we will learn:
1. What is **<mark style="background-color: lightpink">"K-Fold Cross Validation"</mark>**
2. Why we use this to select the best model.

For making a best generalized model, we split the whole dataset into three parts:

1. Training dataset (for training a model)
2. Validation dataset (for finding a best model)
3. Testing dataset (for testing the trained model)

![png](/img/posts/cross_validation/data_split.png){:width="700"}

There are **two possible problems** when splitting the whole dataset into three sets:

* **Problem 1**: The number of samples for learning can be drastically reduced.  
* **Problem 2**: The randomly chosen training and validation dataset can be not representative enough for all dataset.  

**SOLUTION**: 
1. We need **more training dataset** for learning.
2. We need use **various parts of the training and validation dataset**. 


For this, we can use **cross-validation**. 

**<mark style="background-color: lightpink">"K-Fold Cross Validation"</mark>** is one of the cross-validation techniques that we can use.

With this method, the training set is split into subsets by "folding".  
As a result, we are having **K number of folds**.     
Then we are using **one fold** as **a validation dataset** to find the best model.  
The rest **K-1 folds** are used for **training the models**.   

Let's say we are using **"5-fold cross-validation"** for selecting the best model:

![png](/img/posts/cross_validation/cross_validation.png){:width="800"}

Using cross validation method, we could learn more while iterating 5 times compared to the data splitting method in the first image above.   
Furthermore, we could use various parts of the training and validation dataset for learning and validating the performance of the trained model in order to find the best model. 

**A test dataset** is held out **for final evaluation** of the best model that is chosen by the cross validation. 

In the next post, we will learn:
1. What is exatly a good model in terms of machine learning. 
2. How we do **<mark style="background-color: lightblue">hyperparameter tuning</mark>** of a model to find the best model. 

<br/>

#### References

* Reference1: [3.1. Cross-validation: evaluating estimator performance](https://scikit-learn.org/stable/modules/cross_validation.html)
* Reference2: [Hold-out Method for Training Machine Learning Models](https://vitalflux.com/hold-out-method-for-training-machine-learning-model/) 
* Reference3: [Model Selection with Cross Validation](https://harvard-iacs.github.io/2021-CS109A/lectures/lecture05/presentation/ModelSelection_withCV.pdf)
* Reference4: [Evaluation Methods (hold-out, k-fold, confusion matrix...)(in Korean)](https://m.blog.naver.com/myksh0903/222110413015)
* Reference5: [Train, Validation, and Test Set(in Korean)](https://pozalabs.github.io/Dataset_Splitting/)
