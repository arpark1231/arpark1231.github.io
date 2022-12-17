---
layout: post
title: "High precision & Low recall vs. Low precision & High recall"
subtitle: "Assessing the model performance in terms of Precision & Recall"
background: '/img/posts/precision_recall/perfomance.jpg'
---

# High precision & Low recall vs. Low precision & High recall 

We've learned how to calculate the macro/weighted average of precision, recall and f1-score for a trained model. 

If you are not sure how to do it,  
check here: [Macro vs. Weighted Average in a Classification Report of scikit-learn](https://arpark1231.github.io/2022/12/15/macro-weighted-avr-scikit-learn.html)  

In this post, we will learn how to assess the model performance in terms of precision and recall.

![png](/img/posts/precision_recall/classification report_cat_fish.png){:width="500"}

At the end of the article, we can answer to the questions: 

1. How we assess a model output with **<mark style="background-color: lightblue">high precision & low recall</mark>**? 
1. How we assess a model output with **<mark style="background-color: lightblue">low precision & high recall</mark>**? 

There are **four possibilities** for **a performance of a model** in terms of **precision** and **recall**:

* **"high precision & high recall"** 
* **"high precision & low recall"**
* **"low precision & high recall"**
* **"low precision & low recall"**  
<br>

### High precision & High recall

This is **the best case** that we can get from our model. 

**High precision & high recall** means that the the model is returning accurate results (high precision) and returning a majority of all positive results (high recall).

Let's say that the goal of our model is to recognize cat images correctly.

As for our model, the output with high precision & high recall means that the model only recognized cat images correctly from other images. 

![png](/img/posts/precision_recall/HP_HR.png){:width="300"}

* **<mark style="background-color: lightblue">High precision</mark>**: a **low** **<mark style="background-color: lightpink">FP</mark>** (False Positive) rate 
* **<mark style="background-color: lightblue">High recall</mark>**: a **low** **<mark style="background-color: lightpink">FN</mark>** (False Negative) rate  
<br>

* **<mark style="background-color: lightpink">FP</mark>** for our model: The model predicted an image as a cat (positive) but it was actually a dog (negative).
* **<mark style="background-color: lightpink">FN</mark>** for our model: The model predicted an image as a fish (negative) but it was actually a cat (positive).

If we see how to calculate the precision & recall, we can understand the meaning of a low FP for high precision and a low FN for high recall:

![png](/img/posts/precision_recall/formula_precision_FP.png){:width="450"}


![png](/img/posts/precision_recall/formula_recall_FN.png){:width="400"}


Not sure what are FP & FN and how to calculate Precision & Recall,  
check here: [Evaluation of a Model for Classification Problem (Part 1)](https://arpark1231.github.io/2022/12/05/evaluation-binary-classification.html)  


### High precision & Low recall

A model with **<mark style="background-color: lightblue">high precision & low recall</mark>** is returning very few results, but most of its predicted labels are correct.

As for our model, it casts a very small but highly specialised net, does not catch a lot of cat, but there is almost only cat in the net:

![png](/img/posts/precision_recall/HP_LR.png){:width="300"}


### Low precision & High recall


A model with **<mark style="background-color: lightblue">low precision & high recall</mark>** returns many results, but most of its predicted labels are incorrect.

As for our model, it casts a very wide net, catches a lot of cats, but also a lot of other images.

![png](/img/posts/precision_recall/LP_HR.png){:width="300"}


### Low precision & Low recall

This is **the least wanted case** that we can get from our model. 

As for our model, it failed to recognize cat images only and its coverage is also low. 

![png](/img/posts/precision_recall/LP_LR.png){:width="300"}

### Recap

We've learned how to assess the performance of a model in terms of precision & recall.

The model's output with **<mark style="background-color: lightblue">high precision & low recall</mark>** means it predicted the instances for a class quite well, but its coverage is not that high.  

The model's output with **<mark style="background-color: lightblue">low precision & high recall</mark>** means its coverage for a class is quite high, but it includes lots of other instances from other classes. 

#### References

* Reference1: [Precision-Recall](https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html)
* Reference2: [Assessing model performance in secrets detection: accuracy, precision & recall explained](https://blog.gitguardian.com/secrets-detection-accuracy-precision-recall-explained/) 
* Reference3: [Explaining precision and recall](https://medium.com/@klintcho/explaining-precision-and-recall-c770eb9c69e9)
