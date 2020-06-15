---
title: Introduction to CRISP-DM
teaching: 30
exercises: 0
questions:
- "How to approach a seemingly chaotic data analytics problem?"
- "What is the most time consuming step in CRISP-DM?"
objectives:
- "Understand the CRISP-DM framework."
keypoints:
- "The importance of business understanding is always overlooked."
- "Data preparation is least liked, most time consuming task"
- "CRISP-DM is an iterative process."
---

## CRISP-DM

There are lot of proceduralizations of data analytics and data mining which have been devised; of these we consider CRISP-DM to be representative.  CRISP-DM is a cross-industry process model which describes common approaches used by data mining experts.  The components are:

1.  Business Understanding
2.  Data Understanding
3.  Data Preparation
4.  Modeling
5.  Evaluation
6.  Deployment

These steps are generally performed in sequence, but it is often necessary to backtrack to previous steps and repeat certain tasks.

![crisp-dm](../pic/CRISP-DM_Process_Diagram.png){:height="500px"}

### Business understanding

All projects begin with business understanding, motivating the project itself. This initial phase focuses on:

- Understanding the business ramifications
- Understanding the project objectives and requirements from a business perspective
- Converting this knowledge into a data analytics problem definition
- Constructing a preliminary plan designed to achieve the objectives

This may be provided to you, or you may work alone or in teams to generate this motivation and objectives.

### Data understanding

The data understanding phase includes:

- Considering data requirements
- Conducting initial data collection
- Becoming familiar with the data
- Identifying data quality problems and discovering first insights into the data

Business data has various format and often stored in different ways. It may be stored in relational database, or files with different formats. The data can be well structured but often very messy, which leads to next step, data preparation.

### Data preparation

Data preparation encompasses all activities to construct the final dataset, or the data that will be fed into the modeling tool(s) from the initial raw data.  Data preparation tasks are likely to be performed multiple times, and not in any prescribed order.  Tasks include table, record, and attribute selection as well as transformation and cleaning of data for modeling tools. Data preparation is most time consuming task.  It accounts for about three quarters of a data analyst's work. The steps of data preparation include:

- Data acquisition(from database, files, etc)
- Data cleaning(identify and fix errors in data, deal with missing data, etc)
- Data integration(merge different datasets)
- Data transformation and enrichment(create new features from existing features)

You have already examined data preparation techniques and have been warned that these may constitute the lion's share of your work.

### Modeling

In this phase, various modeling techniques are selected and applied, and their parameters are calibrated to optimal values.  Typically, there are several techniques available for solving the same data mining problem.  Some techniques have specific requirements on the form of data.  Therefore, stepping back to the data preparation phase is often needed.

Common modeling techniques include:

- Regression (supervised learning)
- Classification (supervised learning)
- Clustering (unsupervised learning)

### Evaluation

At this stage in the project you have built a model (or models) that appears to have reasonably high performance from a data-analytic perspective.  Before making decisions on the basis of the model, it is critical to thoroughly evaluate it and review each of the steps executed to construct the model.  You need to be certain that the model properly achieves the business objectives.  A key objective is to determine if there is some important business issue that has not been sufficiently considered.  At the end of this phase, a decision on the use of the data mining results should be reached.

### Deployment

Creation of the model is generally not the end of the project.  Even if the purpose of the model is to increase knowledge of the data, the knowledge gained will need to be organized and presented in a way that is useful to the customer.  Depending on the requirements, the deployment phase can be as simple as generating a report or as complex as implementing a repeatable data scoring (e.g. segment allocation) or data mining process.  In many cases it will be the customer, not the data analyst, who will carry out the deployment steps.  Even if the analyst deploys the model it is important for the customer to understand up front the actions which will need to be carried out in order to actually make use of the created models.

### Iterating

We may not begin with a lot of domain knowledge, or there might be problems with the data or the model might not be valuable enough to put into production.  CRISP-DM should not be considered a linear path from project kick-off to deployment.  Remember to go back a step from time to time.  The process equips you upfront to explain to managers what their procedural expectations should be.
