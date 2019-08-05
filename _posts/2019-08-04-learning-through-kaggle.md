---
layout: post
title: My learning journey with the 2019 IEEE Fraud Detection Kaggle Competition
subtitle: One neophyte
bigimg: /img/path.jpg
gh-repo: andre-sav/ieee_fraud
gh-badge: [star, fork, follow]
tags: [Kaggle, machine learning]
---

Machine learning is an exciting field. That is a near-universal truth. Involved in it are some of the greatest minds of the 21st century. Practitioners are the architects of the future in some ways. The uses are multifarious, and one may hope only good comes of it. Sadly much of it is used to propagate the attention economy, and deliver targeted ads to bewildered users.

With the current state of affairs in an ultimately capitalistic world, the ideal scenario is one in which the goals of the corporate entities and the end consumer truly align. Such is the case with the Vesta Corporation’s e-commerce dataset which was submitted for a Kaggle Competition. The goal of the predictive model, in this case, is to classify whether a transaction is fraudulent or not. The benefits are extensive, benefiting all involved aside from the individual(s) committing the fraud, for whom we have no sympathy as they are the bad actors.

This is a difficult problem to solve due to the imbalanced nature of the data. Less than 4% of the transactions therein are fraudulent. Currently, the top submissions are approximating 95% accuracy. This doesn’t tell the whole story, because the way in which the models are inaccurate is very important. If one of the current top models were deployed, there would be big problems with the false negatives as they would be completely off the radar only to be discovered after economic damage has been wrought, potentially irreversibly. False positives are the lesser evil here, as they pose a minor inconvenience, generally in the form of an automated contact with the instigator of the transaction to authenticate it. 
 
I first resolved to make a baseline to beat by using the H2O autoML software. This gave me an accuracy of approximately 87% via XGBoost. however, it is possible to achieve 93% + if trained for longer durations with the proper setup. Good news upon inspecting the confusion matrix produced by H2O is it looked to be that the false negatives are in the minority, the majority of error being false positives.

Initially, my goal was to test the limits of automatic machine learning frameworks. Getting a model going with H2O is not too difficult. Improving upon said model is. I attempted multiple avenues of feature engineering, and parameter adjustments only to see no improvement or failure to execute. At this time auto ml modalities are still in the early phases of development, the open-source variants mainly useful for baseline predictive modeling and applications in which the absolute highest accuracy possible is not necessary. At one point, I began running into technical difficulties making it too costly to proceed. You can view the basic executable code at the bottom of the linked jupyter notebook. 

So, I endeavored to use the top-performing machine learning model, LGBM, to continue my learning process. As a machine learning neophyte, this was easier said than done. Having used H2O and its relative, driverlessAI, which abstracted much of the process beyond installation and configuration, using complex manually tuned models was difficult. Many a time I implemented code that responded with incompatibility which I then had to troubleshoot, giving up and restarting several epochs in the process. Complete system hang-up is par the course here. In the process, I gleaned the importance of time series analysis by visualizing the distribution of the data. This helped to engineer some of the most important features for my model. 

![distribution](https://github.com/andre-sav/ieee_fraud/blob/master/distribution.jpg)

Eventually settling on a functioning variant of LGBM, I was able to come within a few percentage points to the top submission score on Kaggle. Unfortunately, the confusion matrix for this model appears to lean towards false negatives.

![confusion-matrix](https://raw.githubusercontent.com/andre-sav/ieee_fraud/master/confusion.jpg)

Somewhat controversial in the sphere of machine learning is the topic of model interpretability. Some models are considered “black boxes” whose methods are not readily explainable. This is particularly true for neural networks as they are extremely complex. To address this there are several visualization tools one may employ. One of these is the venerable feature importance graph.

![feature-importances](https://raw.githubusercontent.com/andre-sav/ieee_fraud/master/feature_importances.jpg)

This graph portrays the level of influence each particular feature in a model has on the target variable as judged by the model. In the case of binary classification, such as the dataset I worked with, it is how much value the model assigns to each variable to ascertain whether a transaction is fraudulent or not.

In conclusion, I believe this is a great dataset to learn from as it presents a real-world problem with entailing complications. I look forward to learning of the winners and their strategies upon the conclusion of the competition. Perhaps I will try to work with it again in the future after honing my own skillset. 


