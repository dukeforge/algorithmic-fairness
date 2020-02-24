# Algorithmic Fairness Tools Review

## Overview
A guide through some publicly available algorithmic fairness tools (Google's What If, IBM's Fairness 360, and Aequitas).

## Purpose
Data is ubiquitous and various stakeholders are using data modeling tools to better understand that data and to make decisions. Currently, there is an unprecidented combination of large data volume, fast and cheap computing resources, and financial, political, and social incentives to answer questions using data. However, with any form of statistical inference comes the potential for error, bias, misrepresentation, and/or opacity (among many other potential pitfalls). Due to the fact that the decisions made from models can cause harm and perpetuate existing social biases, all stakeholders need tools to interrogate data models and evaluate them for instances of such bias. 

## Data
In our approach to evaluation, we decided to assess the algorithmic fairness tools on the same set of data: COMPAS (Correctional Offender Management Profiling for Alternative Sanctions). COMPAS was designed as a tool to predict the risk of recidivism for individuals who have criminal history and/or spent time in jail or prison. The data were used by Northpointe, Inc. to discover the underlying accuracy of their recidivism algorithm and to test whether the algorithm was biased against certain groups. These data are provided by [ProPublica](https://www.propublica.org/datastore/dataset/compas-recidivism-risk-score-data-and-analysis) as part of their reporting on bias in machine learning models. We chose this dataset because each of the three bias evaluation tools had examples that featured this dataset, thus making side-by-side comparisons more valid. 

## Models
Data models can take many shapes and sizes. They range in complexity from classical statistical tools like linear/logistic regression to deep learning models (i.e., deep neural networks). New models are being developed at a rapid pace and the community of researchers contributing to this development is expansive. For simplicity, the goal of any model is to "map" (with a numeric function) a set of input "parameters" (or, variables) to an outcome of interest. In general, we design a model to estimate a way of combining our parameters in such a way that we can reliably make probability statements about the likelihood of a given outcome occurring. In the context of our data source, the model might make a prediction about the risk of whether a person will commit a future crime given characteristics about that individual. This entire process is known as model training. 

## Evaluation
Once we build our model and train it, the final goal is to show it new, unseen data and evaluate its "performance". By performance, we mean using a menu of measurements that help the model-builder understand how good the model is at predicting an outcome (when compared to the actual known outcome of interest). As you will see in our multiple examples, there are a long list of performance metrics. 

But, the entire point of bias evaluation is to also ask a different set of probing questions. There are an additional set of measurements that are used for delving into how specific parameters (e.g., race) influence the model's predicted outcomes. For example, a model might have a True Positive Rate (or, Recall) of 90%, but we might be interested in also asking the question of "How does a given variable impact that performance or the final prediction?" We will get a better idea of these overlapping model metrics as we dive into the different tools. 

## Tools
[Google’s What-If Tool](https://pair-code.github.io/what-if-tool/#demo-panel-all)

[IBM’s Fairness 360](http://aif360.mybluemix.net/)

[Aequitas](http://aequitas.dssg.io)
