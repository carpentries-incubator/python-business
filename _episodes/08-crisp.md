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
Cross-industry standard process for data mining, known as CRISP-DM, is an open standard process model that describes common approaches used by data mining experts. It is one of the most widely-used analytics models. The CRISP-DM model consists of six steps:
- **Business Understanding**
- **Data Understanding**
- **Data Preparation**
- **Modeling**
- **Evaluation**
- **Deployment**

As shown in below figure, these steps are generally performed in sequence but it will be often necessary to backtrack to previous steps and repeat certain tasks.


![crisp-dm](../pic/CRISP-DM_Process_Diagram.png){:height="500px"}

### Business understanding
All projects start with business understanding. This initial phase focuses on:
- Understanding the business
- understanding the project objectives and requirements from a business perspective,
- converting this knowledge into a data analytics problem definition, and
- a preliminary plan designed to achieve the objectives.

The importance of business understanding can never be emphasized too much. Building a fancy model without thourough business understanding is like building a powerful car without steering wheel.

The ways to gather business knowledge include:
- Online resources
- Document provided by customers
- Talking to business insiders(ie. customer employees)

You will need to assess current situation and set up objectives. Then produce project plan and assess tools and techniques used in following processes.

### Data understanding
The second state of CRISP-DM is data understanding. The data understanding phase includes:
- considering data requirements
- conducting initial data collection
- getting familiar with the data
- identifying data quality problems and discovering first insights into the data

Business data has various format and often stored in different ways. It may be stored in relational database, or files with different formats. The data can be well structured but often very messy, which leads to next step, data preparation.

### Data preparation
The data preparation phase covers all activities to construct the final dataset (data that will be fed into the modeling tool(s)) from the initial raw data. Data preparation tasks are likely to be performed multiple times, and not in any prescribed order. Tasks include table, record, and attribute selection as well as transformation and cleaning of data for modeling tools. Data preparation is most time consuming task. It accounts for about three quarters of a data analyst's work. The steps of data preparation include:

- data acquisition(from database, files, etc)
- data cleaning(identify and fix errors in data, deal with missing data, etc)
- data integration(merge different datasets)
- data transformation and enrichment(create new features from existing features)

We will introduce common data preparation techniques in next session.

### Modeling
In this phase, various modeling techniques are selected and applied, and their parameters are calibrated to optimal values. Typically, there are several techniques for the same data mining problem type. Some techniques have specific requirements on the form of data. Therefore, stepping back to the data preparation phase is often needed.

Common modeling techniques include:
- regression (supervised learning)
- classification (supervised learning)
- clustering (unsupervised learning)

### Evaluation

At this stage in the project you have built a model (or models) that appears to have high quality, from a data analysis perspective. Before proceeding to final deployment of the model, it is important to more thoroughly evaluate the model, and review the steps executed to construct the model, to be certain it properly achieves the business objectives. A key objective is to determine if there is some important business issue that has not been sufficiently considered. At the end of this phase, a decision on the use of the data mining results should be reached.

### Deployment

Creation of the model is generally not the end of the project. Even if the purpose of the model is to increase knowledge of the data, the knowledge gained will need to be organized and presented in a way that is useful to the customer. Depending on the requirements, the deployment phase can be as simple as generating a report or as complex as implementing a repeatable data scoring (e.g. segment allocation) or data mining process. In many cases it will be the customer, not the data analyst, who will carry out the deployment steps. Even if the analyst deploys the model it is important for the customer to understand up front the actions which will need to be carried out in order to actually make use of the created models.

## ITERATIVE
Within a given project, we know that at the beginning of our first ever project we may not have a lot of domain knowledge, or there might be problems with the data or the model might not be valuable enough to put into production. These things happen, and the really nice thing about the CRISP-DM model is it allows for us to do that. It’s not a single linear path from project kick-off to deployment. It helps you remember not to beat yourself up over having to go back a step. It also equips you with something upfront to explain to managers that sometimes you will need to bounce between some phases, and that’s ok.
