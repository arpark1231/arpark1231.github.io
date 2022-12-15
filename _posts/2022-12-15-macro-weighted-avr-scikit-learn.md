---
layout: post
title: "Macro vs. Weighted Average in a Classification Report of scikit-learn"
subtitle: "What is the difference and how to calculate them?"
background: '/img/posts/evaluation_part1/assessment-strategy-evaluation-prioritize-icons.jpg'
---

# Macro vs. Weighted Average in a Classification Report of scikit-learn

We've learned how to evaluate the performance of a trained model for multiclass classfication problem.  
And the way we calculated the average of precision and recall are called "Macro Average". 

If you are not sure how we can evalute a trained model for multiclass classification problem,  
check here: [Evaluation of a model for classification problem (Part 2)](https://arpark1231.github.io/2022/12/07/evaluation-multiclass-classification.html)  

With **"Macro averaging"**, we calculate the avarage of a metrics **without concerning the weights of each class**.

But what if the training data are **imbalanced** per class?  
For this case we use **"Weighted averaging"** method.  

In this post, we will see the **difference between Macro and Weighted average** using the **"Classification Report"** provided by scikit-learn.

![png](/img/posts/macro_weighted_avr/classification_report_overview.png){:width="400"}

At the end of the article, we can answer to the questions: 

1. How can we read **<mark style="background-color: lightblue">Classification Report</mark>** from scikit-learn? 
2. How can we calculate **<mark style="background-color: lightpink">Macro average</mark>** and **<mark style="background-color: lightpink">Weighted average</mark>** of three metrics: **"Precision"**, **"Recall"** and **"F1-score"**? 

## Multiclass Classification Problem

For the multiclass classification problem, we have a **"image recognizer"** for animals as our trained model.    
The goal of our model is to recognize images according to types of animals.

We have total **three types of animals** to be recognized:   

* **CLASS 1**: "Cat" 
* **CLASS 2**: "Fish" 
* **CLASS 3**: "Dog"

The following confusion matrix shows that our trained model classified **total 25 images** (sum of all cells) **according to three classes**.

If you are not sure about what the **confusion matrix** is about,  
check here: [Evaluation of a model for classification problem (Part 1)](https://arpark1231.github.io/2022/12/05/evaluation-binary-classification.html)  
<br>
![png](/img/posts/macro_weighted_avr/confusion_matrix_overview.png){:width="400"}
<br>
<br>

With the **Classification Report** in scikit-learn, we can calculate the performance of the trained model based on the confusion matrix:


```python
from sklearn.metrics import classification_report

# "y_pred" corresponds to the vertical line of the confusion matrix above ("PREDICTED VALUE") 
y_pred = ["cat", "cat", "cat", "cat", "cat", "cat", "fish", "fish", "fish", "fish", "fish", "fish", "fish", 
          "fish", "fish", "fish", "dog", "dog", "dog", "dog", "dog", "dog", "dog", "dog", "dog"]

# "y_true" corresponds to the horizontal line of the confusion matrix above ("ACTUAL VALUE") 
y_true = ["cat", "cat", "cat", "cat", "fish", "dog", "cat", "cat", "cat", "cat", "cat", "cat", "fish", "fish", 
          "dog", "dog", "cat", "cat", "cat", "dog", "dog", "dog", "dog", "dog", "dog"]

print(classification_report(y_true, y_pred, labels=["cat", "fish", "dog"]))
```

                  precision    recall  f1-score   support
    
             cat       0.67      0.31      0.42        13
            fish       0.20      0.67      0.31         3
             dog       0.67      0.67      0.67         9
    
        accuracy                           0.48        25
       macro avg       0.51      0.55      0.47        25
    weighted avg       0.61      0.48      0.50        25


### Macro average of Precision, Recall, F1-score
 
There are three metrics to evaluate the performace of a trained model in the classification report:  
"Precision", "Recall" and "F1-score".
 
We've already learned how we calculate the macro average of the metrics.
 
Since we have **three classes** for our trained model, we **devide the sum of the values by three** for calculating **macro avarage**.

Let's review quickly how we calculated macro average of precision, recall and f1-score for our trained model.

### Macro average of Precision

**<mark style="background-color: lightpink">Precision</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all PREDICTED positive** cases.  

![png](/img/posts/macro_weighted_avr/precision_macro_avr.png){:width="400"}

We calculate the macro average of the precision for our trained model as follows: 

![png](/img/posts/macro_weighted_avr/precision_macro_avr_formula.png){:width="300"}
<br>

The precision of each class and the **<mark style="background-color: lightpink">Macro average</mark>** of them can be found in the **<mark style="background-color: lightblue">classification report</mark>**:

![png](/img/posts/macro_weighted_avr/classification_report_precision_macro.png){:width="400"}
<br>  

### Macro average of Recall

**<mark style="background-color: lightpink">"Recall"</mark>** is the ratio of **correctly IDENTIFIED positive** cases to **all ACTUAL positive** cases.   

![png](/img/posts/macro_weighted_avr/recall_macro_avr.png){:width="500"}

We calculate the macro average of the recall for our trained model as follows: 

![png](/img/posts/macro_weighted_avr/recall_macro_avr_formula.png){:width="300"}
<br>

The recall of each class and the **<mark style="background-color: lightpink">Macro average</mark>** of them can be found in the **<mark style="background-color: lightblue">classification report</mark>**:

![png](/img/posts/macro_weighted_avr/classification_report_recall_macro.png){:width="400"}

### Macro average of F1-Score

**<mark style="background-color: lightpink">"F1-Score"</mark>** is the harmonic mean of **"Precision"** and **"Recall"** as we can see in the formula:

![png](/img/posts/macro_weighted_avr/f1_formula.png){:width="300"}
<br>

We calculate the macro average of the f1-score for our trained model as follows: 

![png](/img/posts/macro_weighted_avr/f1_macro_formula.png){:width="300"}
<br>

The f1-score of each class and the **<mark style="background-color: lightpink">Macro average</mark>** of them can be found in the **<mark style="background-color: lightblue">classification report</mark>**:

![png](/img/posts/macro_weighted_avr/classification_report_f1_macro.png){:width="400"}

### Weighted Average 

**<mark style="background-color: lightpink">Weighted average</mark>** is a calculation that takes into account the varying degrees of importance of the numbers in a data set.  

Since the weighted average takes into account the weight of each class, it can be **more accurate than a macro avarage**, which are simply caculated assuming the identical weight of each class.

Weighted average is especially **useful for imbalanced dataset per class**.

How do we know that our dataset is imbalanced?

We can check the **"support"** in the **<mark style="background-color: lightblue">classification report</mark>**.

![png](/img/posts/macro_weighted_avr/classification_report_support.png){:width="400"}

**"Support"** refers to the number of actual occurrences of the class in the dataset.  

For example, the support value of **<span style="color:blue">"3"</span>** for the class **<span style="color:blue">"fish"</span>** means that there is only **<span style="color:blue">three actual occurences</span>** of the class, which corresponds to the blue marked cells in the confusion matrix below:

![png](/img/posts/macro_weighted_avr/support_fish.png){:width="400"}

And **the total number of training samples** is **"25"** for every class, as it is also shown in the classification report below:

![png](/img/posts/macro_weighted_avr/classification_report_support2.png){:width="400"}

### Weight of each class

Our training dataset is imbalanced because the actual occurences are quite different per class, as shown in the classification report.

Then how we can calculate the weight of each class?

The **"weight"** essentially refers to the proportion of each class’s support relative to the sum of all support values.


We just can devide the actual occurences by the total number of training samples per class as follows:

![png](/img/posts/macro_weighted_avr/classification_report_weight_per_class.png){:width="500"}

**Higher weight** for a class like "cat" ("0.52") means it has **higher importance** than other classes while **lower weight** for a class like "fish" ("0.12") means it has **lower importance** than other classes when training the model.

### Weighted Average of F1-score

If we learn how to calculate the weighted average of F1-score, we can also calculate it for precision and recall.  
So let's focus on the weighted average f1-score.

We can calculate **<mark style="background-color: lightpink">the weighted average</mark>** of **<mark style="background-color: lightpink">f1-score</mark>** by multiplying the f1-score with the weight for each class and summing them up:

![png](/img/posts/macro_weighted_avr/classification_report_weighted_f1.png){:width="700"}

### Recap

We've learned how to evaluate the macro and weighted avearage of three metrics for our trained model.

**<mark style="background-color: lightpink">Macro averaging</mark>** is the averaging method **assuming the identical weights of each class** while **<mark style="background-color: lightpink">weighted averaging</mark>** is the averaging method **taking into account the weights of each class**.

Try to calculate the weigted average of precision and recall for our trained model and compare the results with the classification report above.

Hope you enjoy the journey :)

#### References

* Reference1: [Micro, Macro & Weighted Averages of F1 Score, Clearly Explained](https://towardsdatascience.com/micro-macro-weighted-averages-of-f1-score-clearly-explained-b603420b292f#989c)
* Reference2: [sklearn.metrics.classification_report](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html) 
* Reference3: [Classification Report](https://www.scikit-yb.org/en/latest/api/classifier/classification_report.html)
* Reference4: [Weighted Average: What Is It, How Is It Calculated and Used?](https://www.investopedia.com/terms/w/weightedaverage.asp)
