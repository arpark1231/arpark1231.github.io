---
layout: post
title: "Evaluation of a Model for Classification Problem (Part 1)"
subtitle: "Binary Classification"
background: '/img/posts/01.jpg'
---

# Evaluation of a model for classification problem (Part 1)

How do we evaluate the quality of a trained model? In classification problems, we can check how often a class is predicted correctly by the model. In the part 1, we first deal with the binary classification problem, which will be the base for the multiclass classification problem in the part 2.  

At the end of the article, we can answer to the questions:
1. What are **<mark style="background-color: yellow">"TP"</mark>**, **<mark style="background-color: yellow">"FP"</mark>**, **<mark style="background-color: yellow">"FN"</mark>** and **<mark style="background-color: yellow">"TN"</mark>** in a **<mark style="background-color: pink">"Confusion Matrix"</mark>**?
2. What are **<mark style="background-color: lightblue">"Accuracy"</mark>** (Bonus: **<mark style="background-color: lightpurple">"Accuracy Pardox"</mark>**), **<mark style="background-color: lightblue">"Precision"</mark>**, **<mark style="background-color: lightblue">"Recall"</mark>** and **<mark style="background-color: lightblue">"F1-Score"</mark>**?

## Binary Classification

The goal of a model for a binary classification problem is to classify two classes well. 

For example, we can imagine that our model is **a rapid testkit for corona virus**, which are designed to detect a person who has corona virus.  
Then, **two classes** for the model are:  

* **CLASS 1**: "has Corona" (positive) 
* **CLASS 2**: "has no Corona" (negative)  

For the two classes, there are **four cases** resulting by the testkit.

* **CASE 1**: The result of the testkit is positive AND the person has actually corona virus &rightarrow; **<mark style="background-color: yellow">"TP"</mark>** (**T**rue **P**ositive)  
* **CASE 2**: The result of the testkit is positive BUT the person does not have corona virus &rightarrow; **<mark style="background-color: yellow">"FP"</mark>** (**F**alse **P**ositive)  
* **CASE 3**: The result of the testkit is negative BUT the person has actually corona virus &rightarrow; **<mark style="background-color: yellow">"FN"</mark>** (**F**alse **N**egative)  
* **CASE 4**: The result of the testkit is negative AND the person does not have corona virus &rightarrow; **<mark style="background-color: yellow">"TN"</mark>** (**T**rue **N**egative)  

<!--<p align = "left"><img src = img/posts/evaluation_part1/confusion_matrix2.png width = "400"></p>-->

![png](/img/posts/evaluation_part1/confusion_matrix2.png){:width="600"}

The images above are called **<mark style="background-color: pink">"Confusion Matrix"</mark>** and we can easily see the four cases mentioned above in the each cell of the confusion matrix.  

For the purpose of the testkit, **the case 1** and **the case 4** are **the right predictions** by the model because it detected the person who has actually corona virus **<mark style="background-color: yellow">(TP)</mark>** and the person who does not have corona virus **<mark style="background-color: yellow">(TN)</mark>** correctly. **<span style="color:green">The right predictions</span>** by the model are marked **<span style="color:green">GREEN</span>** in the confusion matrix.  

**The case 2** and **the case 3** are **the wrong predictions** by the model becaus it predicted wrong that the person who does not have corona virus as positive **<mark style="background-color: yellow">(FP)</mark>** and who does have corona virus as negative **<mark style="background-color: yellow">(FN)</mark>**. **<span style="color:orange">The wrong predictions</span>** by the model are marked **<span style="color:orange">ORANGE</span>** in the confusion matrix.

**With the confusion matrix**, we can simply visualize how to calculate the four metrics **"Accuracy"**, **"Precision"**, **"Recall"**, and **"F1-Score"** in order to evaluate the performance of the trained model.  

The following confusion matrix shows the four cases with their number of instances by the model:

<!--<p align = "left"><img src = "evaluation of the binary calssification/confusion_matrix3.png" width = "400"></p>-->
![png](/img/posts/evaluation_part1/confusion_matrix3.png){:width="600"}

The total number of the predicted instances are 10,000, which is the sum of the four cells.  

**Total number of instances**: **TP**(9040) **+** **FP**(151) **+** **FN**(68) + **TN**(741) **=** **10,000**

Now we are going to learn what are exactly the four metrics and how we calculate them. 

### Accuracy

**<mark style="background-color: lightblue">"Accuracy"</mark>** tells us how many **correct predictions** are made **from the total predictions**.  

**Correct predictions** for the corona testkit are **TP**(9040) and **TN**(741).  
**Total predictions** by the testkit are **TP**(9040) **+** **FP**(151) **+** **FN**(68) + **TN**(741)  

<!--<p align = "left"><img src = "evaluation of the binary calssification/confusion_matrix_accuracy.png" width = "400"></p>--> 
![png](/img/posts/evaluation_part1/confusion_matrix_accuracy.png){:width="600"}

This is the formula how we calculate the accuracy:

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_accuracy.png" width = "300"></p>-->   
![png](/img/posts/evaluation_part1/formula_accuracy.png){:width="400"}

And this is the accuracy of our model: 

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_accuracy_model.png" width = "450"></p>-->  
![png](/img/posts/evaluation_part1/formula_accuracy_model.png){:width="550"}

Accuracy seems like a quite simple and good metric to evaluate the performance of a model.  
But there are tricky cases to evaluate a model only with Accuracy.

### Accuracy Paradox

Let's assume that our model is **spam email filter**.  

We have **two models** for the spam filter.  
What are the **accuracy** of the two models?  


<!--<p align = "left"><img src = "evaluation of the binary calssification/CM_spam_filter_model1.png" width = "400"></p>--> 
![png](/img/posts/evaluation_part1/CM_spam_filter_model1.png){:width="600"}

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_accuracy_M1.png" width = "300"></p>-->  
![png](/img/posts/evaluation_part1/formula_accuracy_M1.png){:width="450"}
<br>
<br>
<!--<p align = "left"><img src = "evaluation of the binary calssification/CM_spam_filter_model2.png" width = "400"></p>--> 
![png](/img/posts/evaluation_part1/CM_spam_filter_model2.png){:width="600"}

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_accuracy_M2.png" width = "300"></p>-->  
![png](/img/posts/evaluation_part1/formula_accuracy_M2.png){:width="450"}

The accuracy of the two models **"Accuracy_M1"** and **"Accuracy_M2"** are the **same** as **"0.95"** even if the second model could not detect any spam email  
(**no "TP"**), which is actually its main purpose.  
<br>
The **<mark style="background-color: lightpurple">"Accuracy Pardox"</mark>** is the paradoxical finding that accuracy is actually not a good metric for predictive models of classification problems. 

So we need **other metrics** for evaluation of a classification model.  
Let's go back to our **corona testkit model**.


### Precision

**<mark style="background-color: lightblue">"Precision"</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all PREDICTED positive** cases.  
For Precision, we can focus on **the vertical line** of the follwing **confusion matrix**:

<!--<p align = "left"><img src = "evaluation of the binary calssification/confusion_matrix_precision.png" width = "400"></p>-->
![png](/img/posts/evaluation_part1/confusion_matrix_precision.png){:width="600"}

This is the formula how we calculate the precision:

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_precision.png" width = "200"></p>--> 
![png](/img/posts/evaluation_part1/formula_precision.png){:width="300"}

And this is the precision of our model: 

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_precision_model.png" width = "320"></p>-->
![png](/img/posts/evaluation_part1/formula_precision_model.png){:width="460"}
<br>

For our testkit model, **Precision "1"** means that the model gave the positive results only for people who actually have corona virus.


### Recall

**<mark style="background-color: lightblue">"Recall"</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all ACTUAL positive** cases.  
For Recall, we can focus on **the horizontal line** of the follwing **confusion matrix**:

<!--<p align = "left"><img src = "evaluation of the binary calssification/confusion_matrix_recall.png" width = "400"></p>-->
![png](/img/posts/evaluation_part1/confusion_matrix_recall.png){:width="600"}

This is the formula how we calculate the precision:

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_recall.png" width = "200"></p>-->  
![png](/img/posts/evaluation_part1/formula_recall.png){:width="280"}

And this is the precision of our model: 

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_recall_model.png" width = "280"></p>--> 
![png](/img/posts/evaluation_part1/formula_recall_model.png){:width="420"}
<br>

For our testkit model, **Recall "1"** means model does not wrongly predict people who does not have corona as positive.

### F1-Score

Actually we want to know both of them:  
**1.** if a model identifies all of our positive cases (from **"Precision"**)  <br>
**2.** if the model at the same time identifies only positive cases (from **"Recall"**)    


**<mark style="background-color: lightblue">"F1-Score"</mark>** is the harmonic mean of **<mark style="background-color: lightblue">"Precision"</mark>** and **<mark style="background-color: lightblue">"Recall"</mark>** as we can see in the formula:

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_f1-score.png" width = "320"></p>-->
![png](/img/posts/evaluation_part1/formula_f1-score.png){:width="450"}

And this is the F1-Score of our model: 

<!--<p align = "left"><img src = "evaluation of the binary calssification/formula_f1-score_model.png" width = "360"></p>--> 
![png](/img/posts/evaluation_part1/formula_f1-score_model.png){:width="520"}

Since we know how to evaluate a model for binary classification, now we can **evaluate** a model for **multiclass classification**.

#### References

* Reference1: [Evaluation of Model (in German)](https://michaelkipp.de/deeplearning/3_Maschinelles_Lernen_II.html#Evaluation-von-Modellen)  
* Reference2: [Metrics for Evaluation (in German)](https://www.python-kurs.eu/metriken.php)
