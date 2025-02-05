---
layout: post
title: "Evaluation of a Model for Classification Problem (Part 2)"
subtitle: "Multiclass Classification"
background: '/img/posts/evaluation_part1/assessment-strategy-evaluation-prioritize-icons.jpg'
---

# Evaluation of a model for classification problem (Part 2)

How do we evaluate the quality of a trained model?  

In classification problems, we can check how often a class is predicted correctly by the model.  

In the part 1 of this series, we already dealt with the binary classification problem, which is the base for the multiclass classification problem in part 2.  

If you are not sure how we can evalute a trained model for binary classification problem, check here: [Evaluation of a model for classification problem (Part 1)](https://arpark1231.github.io/2022/12/05/evaluation-binary-classification.html)  

At the end of the article, we can answer to the questions: 

1. How can we see **multicalss classfication** as **multiple binary classification** using **<mark style="background-color: lightpurple">One-vs-Rest(OvR) method</mark>**?
2. How can we **evaluate** a peformance of a trained model for **muticlass classification** using **<mark style="background-color: lightblue">"Accuracy"</mark>**, **<mark style="background-color: lightblue">"Precision"</mark>**, **<mark style="background-color: lightblue">"Recall"</mark>** (Bonus: **<mark style="background-color: lightpink">Micro averaging</mark>** of Precision and Recall) with **"Confusion Matrix"?**
 

## Multiclass Classification

The goal of a model for a muticlass classification problem is to classify each class in the muticlass well.  
If we focus on **one class**, it is actually **same with binary class**. 

Let's say that we have **"image recognizer"** for animals as our trained model.   
The goal of our model is to recognize images according to the types of animals.

We have total **three types of animals** to be recognized:   

* **CLASS 1**: "Cat" 
* **CLASS 2**: "Fish" 
* **CLASS 3**: "Dog"

Then how can we evaluate our trained model for those three classes?

### One-vs-Rest(OvR) method

We can see the multiclass classification problem as multiple binary classification problems using One-vs-Rest method.  

**<mark style="background-color: lightpurple">One-vs-rest (OvR)</mark>** is a heuristic method for using binary classification algorithms for multiclass classification.

The following confusion matrix shows that our trained model classified **total 25 images** (sum of all cells) **by three classes**.
<br>
<br>
![png](/img/posts/evaluation_part2/confusion_matrix.png){:width="400"}
<br>
<br>

If we focus on the first class "Cat", then we can see the multiclass classification problem as a binary classification problem,  
such as **"Cat"** **<mark style="background-color: lightpurple">(*One*)</mark>** **vs.** **"Not cat"** **<mark style="background-color: lightpurple">(*Rest*)</mark>** as shown in the following confusion matrix:

![png](/img/posts/evaluation_part2/confusion_matrix_OvR.png){:width="500"} 

We can use the OvR method for each class. 

Then **the multiclass classification problem** can be divided into **three binary classifications** as follows:

* **Binary Classification Problem 1**: Cat vs. Not cat [fish, dog]  
* **Binary Classification Problem 2**: Fish vs. Not fish [cat, dog]  
* **Binary Classification Problem 3**: Dog vs Not dog [cat, fish]  

Now we know how we can see a multiclass classification problem as multiple binary classification problems.

Since we know how to evaluate a trained model for a binary classification problem,  
it is easy to evaluate the performance of a trained model for a multiclass classification problem using three metrics (**Accuracy**, **Precision** and **Recall**). 

### Accuracy

**<mark style="background-color: lightblue">"Accuracy"</mark>** tells us how many **correct predictions** are made **from the total predictions**.  

![png](/img/posts/evaluation_part2/confusion_matrix_accuracy.png){:width="500"}

**<span style="color:green">Correct predictions</span>** are the sum of the green cells, while **total predictions** are the sum of all the cells in the confusion matrix.

This is the formula how we calculate the accuracy:

![png](/img/posts/evaluation_part2/formula_accuracy.png){:width="400"}

And this is how we can calculate the accuracy of our trained model: 

![png](/img/posts/evaluation_part2/formula_accuracy_model.png){:width="450"}

For precision and recall we first calculate precision and recall for each class.  
Then we calculate the averages of them over all classes.

### Precision

**<mark style="background-color: lightblue">"Precision"</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all PREDICTED positive** cases.  
For Precision, we can focus on **the vertical line** of the follwing **confusion matrix**:

![png](/img/posts/evaluation_part2/confusion_matrix_precision_new.png){:width="500"}

For our trained model, we need to calculate three precisions for each class then divide the sum of them by 3.

This is the formula how we calculate the precision:

![png](/img/posts/evaluation_part2/formula_precision.png){:width="250"}

And this is the precision of our model: 

![png](/img/posts/evaluation_part2/formula_precision_model.png){:width="350"}
<br>

### Recall

**<mark style="background-color: lightblue">"Recall"</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all ACTUAL positive** cases.  
For Recall, we can focus on **the horizontal line** of the follwing **confusion matrix**:

![png](/img/posts/evaluation_part2/confusion_matrix_recall_new.png){:width="600"}

For our trained model, we need to calculate three recalls for each class then divide the sum of them by 3.

This is the formula how we calculate the precision:

![png](/img/posts/evaluation_part2/formula_recall.png){:width="250"}

And this is the precision of our model: 

![png](/img/posts/evaluation_part2/formula_recall_model.png){:width="350"}
<br>

We've learned how to evaluate the performance of our trained model for multiclass classfication problem.  
And the way we calculate the average of precision and recall are called "Macro Average". 

**<mark style="background-color: lightpink">Macro averaging</mark>** is perhaps the most straightforward among the numerous averaging methods, in which we calculate the avarage of the multiclass **without concerning the weights of the classes**.

What if the dataset is imbalanced per classes?  
And what about F1-Score that we used for binary classfication problem?

In the next post, we will learn about **<mark style="background-color: pink"> Weighted averaging</mark>** of the metrics fo evaluation of a trained model **for multiclass classification**.

#### References
 
* Reference1: [3.2 Multicalss Classification (in German)](https://michaelkipp.de/deeplearning/3_Maschinelles_Lernen_II.html#Evaluation-von-Modellen) 
* Reference2: [Multi-Class Metrics](https://towardsdatascience.com/multi-class-metrics-made-simple-part-i-precision-and-recall-9250280bddc2)
* Reference3: [One-vs-Rest for Multiclass Classification](https://machinelearningmastery.com/one-vs-rest-and-one-vs-one-for-multi-class-classification/)
* Reference4: [Choosing Performance Metrics](https://towardsdatascience.com/choosing-performance-metrics-61b40819eae1)
