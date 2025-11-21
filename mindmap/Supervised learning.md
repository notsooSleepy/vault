---
tags:
  - adault
aliases:
  - discriminative model
---
2025-11-17 19:30
# Supervised learning
## Training data
* Target variable/variables 
	* Labels
* Observations/Examples
* Features
![[Pasted image 20251118192120.png|600]]
## ML workflow
### 1. Raw data
### 2. Extract features
### 3. Split dataset
* **Train dataset**
* **Test dataset**
### 4. Train ML model with **train dataset**
### 5. Evaluate with **test dataset**
* ways to evaluate
	* what is the average error of the predictions?
	* what percentage of apartments did the model accurately predict within a 10% margin
#### overfitting
* for Classification
* performs great on training data
* performs poorly on testing data
* model memorized training data and can't generalize learning's to new data
* use testing set to check model performance
![[Pasted image 20251119184930.png|600]]
#### accuracy
* for Classification
* correctly classified observations / all observations
* 48 / 50 = 96%
#### confusion matrix
* for Classification
* true positives
* false negatives
* false positives
* true negatives
![[Pasted image 20251119185834.png|600]]
##### sensitivity
* *focuses on true positives*
![[Pasted image 20251119190040.png|600]]
* optimizing for sensitivity means we'd rather mark legitimate transaction as suspicious than authorize fraudulent transactions.
##### specificity
* *focuses on true negatives*
![[Pasted image 20251119194151.png|600]]
* rather send spam to inbox than send real emails to the spam folder
#### evaluating [[Regression]]
![[Pasted image 20251119192007.png|500]]
### 6. Is performance good enough?
* NO? fine tune it.
#### ways to improve performance
##### dimensionality reduction
* basically it *means reducing the number of features* which seems counter-intuitive but some of the features *maybe carry useless information*
* *keep only one feature when two are correlated* like height and shoe size (usually tall people have big foots)
* *collapse multiple features into one underlying feature* like height and weight into **Body Mass Index**
##### hyperparameter tuning
![[Pasted image 20251119195350.png|600]]
##### ensemble methods
###### classification
* voting
![[Pasted image 20251119195510.png|600]]
###### regression
* averaging
![[Pasted image 20251119195618.png|600]]
# Links
[[Classification]]
[[Regression]]
# References