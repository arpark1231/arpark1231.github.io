---
layout: post
title: "Training, Testing and Validation Datasets in Machine Learning"
subtitle: "What they are and when we use them in terms of ML"
background: '/img/posts/training_testing_validation/ML1.jpg'
---

# Training, Testing and Validation Datasets in Machine Learning

At the end of the article, we can answer to the questions:

1. What are **<mark style="background-color: lightblue">"Training dataset"</mark>**, **<mark style="background-color: lightblue">"Testing dataset"</mark>** and **<mark style="background-color: lightblue">"Validation dataset"</mark>** 
2. When we use them in terms of machine learning?


**The gole of a machine learning** is **to make a general model** by training the model.   
The general model for a classification problem should **classify the unseen data well** that the model never trained on. 

The main key here is to **split the dataset** for the training and the testing because the test of the trained model should be done with **unseen data** from the model.  

If we train and test on the same data, it is like that your trial exam (for training) and the real exam (for testing) are same.  
Then the model cannot predict well when there is new data to be classified (no general model at all).

This is why we split the dataset into two parts: 
1. **<mark style="background-color: lightblue">Training dataset</mark>** (for training a model)
2. **<mark style="background-color: lightblue">Testing set</mark>** (for testing the trained model)

Typically, **80%** of the whole dataset is used for training and **20%** of the dataset for testing (the percentage can vary):

![png](/img/posts/training_testing_validation/data_split1.png){:width="700"}

Then what is validation dataset and when we need it?

**<mark style="background-color: lightblue">Validation dataset</mark>** is used for validating and tuning the model before we test the final trained model.  
When tuning the model, we adjust the hyperparmeters of the model in order to **find the best model** to be evaluated.

We get the validation datset by spliting the whole dataset as follows:

![png](/img/posts/training_testing_validation/data_split2.png){:width="700"}

When the dataset is enough, we normally use **60%** of the data for training, **20%** of the data for validation, and **20%** of the data for testing.

The most important thing by the validation dataset is that the model occasionally **"sees"** this data to fine tune the model, but **never** **“learns”** from the data.

In the next post, we will learn:
1. How we split the dataset when it is not enough. (**<mark style="background-color: lightpink">"K-Fold Cross Validation"</mark>**)
2. Why we adjust the hyperparameters of the model. (The relationship between **<mark style="background-color: lightpink">"epoch"</mark>** and **<mark style="background-color: lightpink">"model's performance"</mark>**)

<br/>

#### References

* Reference1: [About Train, Validation and Test Sets in Machine Learning](https://towardsdatascience.com/train-validation-and-test-sets-72cb40cba9e7)
* Reference2: [
Hold-out Method for Training Machine Learning Models](https://vitalflux.com/hold-out-method-for-training-machine-learning-model/) 
* Reference3: [Cross Validation](https://datamines.de/cross-validation/)
* Reference4: [Evaluation Methods (hold-out, k-fold, confusion matrix...)(in Korean)](https://m.blog.naver.com/myksh0903/222110413015)
* Reference5: [Evaluation Metrics for Classification Models](https://medium.com/analytics-vidhya/evaluation-metrics-for-classification-models-e2f0d8009d69)
* Reference6: [Train, Validation, and Test Set(in Korean)](https://pozalabs.github.io/Dataset_Splitting/)
