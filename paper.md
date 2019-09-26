---
title: 'Data Carpentry for Business (Python and SQL)'
tags:
- Python
- SQL
- RDBMS
- Data Carpentry 
- Business Analytics   
authors:
- name: Robert J Brunner
  orcid: 0000-0002-7892-4460
  affiliation: 1 
- name: Neal Davis
  orcid: 0000-0002-1131-8319
  affiliation: 1 
- name: Jessen Hobson
  orcid: 0000-0001-9748-8070
  affiliation: 1 
- name: Linden Lu
  orcid: 0000-0002-7931-0305
  affiliation: 1 
- name: Hao Xi
  orcid: 0000-0002-9520-5652
  affiliation: 1   
affiliations:
- name: Department of Accountancy, University of Illinois
  index: 1
date: 07 July 2019
bibliography: paper.bib
---   

# Summary
The main purpose of this workshop is to equip business students with relevant data retrieval, programming, and data analytic skills. The workshop contains two parts: the first part focuses on SQL, and the second part focuses on Python. The SQL lessons introduce the basic concepts of relational databases and instruct students how to write efficient queries. For the Python part, the first few lessons cover basic programming concepts such as variables, loops, and functions. Students will also learn how to process data and perform Excel-like tasks by using Python. Moreover, students will be given an overview of the CRISP-DM framework, which is a popular methodology for completing data analytics projects. At the end of the workshop, there are two data analysis case studies that are based on real-life data. The workshop is designed to last two days; the SQL part is expected to take one-half day and the Python part is expected to take one and a half days (See Appendix for details). All materials required to deliver the workshop, such as data, a setup guide, and code, are provided. Practice questions and their solutions are also provided. Workshop instructors are expected to be trained to deliver curriculum from the Data Carpentry. For students who cannot attend the workshop, they may still go through the lessons independently, although this will likely not be as productive as sitting through a live training session.
This workshop has been built on previous work from the Data Carpentry. The SQL lessons are based on“SQL for Ecology” [@Martinez2017] from Data Carpentry; and the Python lessons are based on “Python Novice Inflammation” [@Bostroem2016] from Software Carpentry and “Python for Ecology” [@Gosset2017] from Data Carpentry.
 
# Statement of needs
Traditionally, business students have employed spreadsheet programs such as Microsoft Excel for basic data storage and analysis.  Spreadsheets have served as a workable complement to dedicated business analytics tools such as Alteryx, Tableau, or Qlik.  However, spreadsheet programs, when employed as data analysis tools, are susceptible of several kinds of errors, including:   
1. Inadvertent replacement of a dynamic (updating) formula with a static (fixed) value.
2. In-cell formula errors that are difficult to locate and correct due to A1-style row–column notation.
3. Opacity in interpretation of numerical values due to formatting (such as the number of significant figures).
4. Difficulty of auditing large spreadsheets with many formulas.   

Several authors have noted the difficulty of reliably employing spreadsheets for business [@Powell2009], healthcare [@Dobell2018], and other fields [@Caulkins2007].  In addition, the velocity, volume, and variety of data continues to increase, frequently beyond the in-memory capability of commercially available spreadsheet programs.  In short, realistic data analytics case studies are frequently too challenging for contemporary spreadsheet programs to support, thus a new approach is required to meet the needs of business students.
In response to this scaling problem, many firms employ Python as a solid scalable alternative to spreadsheet programs for data analytics.  Python’s popularity as a data analytics tool is rooted in its clean, beginner-friendly syntax and in a productive cycle of library development, allowing easy completion of many tasks including efficient data cleaning; model building, validation, and deployment; and data visualization.  Coupled with other common tools, such as SQL for database management, Python offers a robust and growing ecosystem of tools for beginners and experts alike.
We have developed a Python-centered curriculum that introduces business students to the principles of data analysis by using Python, the Pandas library, and SQL for database management.  These lessons are curated under the auspices of the Data Carpentry program, which coordinates lesson development and workshops for a variety of domains including ecology, social science, and geospatial information systems. Workshop lessons target competence rather than expertise, expecting students to continue to use reference materials and “computational recipes” in constructing their own solutions for problems within their own domain (for example, Business).   

# Learning objectives and contents 
Our overall learning objective for business students is that they will be able to perform basic data querying, filtering, aggregation, and analysis by using SQL and Python. To this end, the workshop lessons cover database query operations by using SQL, programming basics by using Python, and data analysis by using the “CRoss-Industry Standard Process for Data Mining” (CRISP-DM) framework.  The lessons are structured to guide students gradually from the basic syntax to essential modeling and analysis operations.
## Day 1:  Introduction to SQL and Introduction to Python  
**Scope**: Lesson 1–5 from “SQL for Business” and Lesson 1–6 from “Python for Business”   
**Contents**:  
* **Relational database concepts**   
Relational Database Management Systems (RDBMS) are one of the most popular database models in the industry [@dbe2019]. In this part of the workshop, students will first learn about the limitations of spreadsheets for data storage. Second, the basic concepts of an RDBMS will be introduced to help students understand their advantages over spreadsheets. Students will learn how data are stored within an RDBMS and how the tables are linked together in a relational database.   
* **SQL**   
Structured Query Language (SQL) is a standard language to interact with RDBMS. This part of the workshop will cover querying, filtering, aggregation, and joining operations in a relational database by using SQL. After each topic, students will work on practice questions to strengthen their knowledge. 
* **Elements of Python Programming**   
Basic Python skills such as loading files, loops, functions, and importing libraries are included in the first part of the Python segment of the workshop.  These skills are essential for students to understand how Python works and to prepare them for future lessons.
* **Pandas (Python for Data Analysis)**   
Tabular data is often the most common type of data that business students will be expected to analyze. Pandas is a very popular Python library that can be used to easily handle tabular data from within a Python program. During this part of the course, students will learn how to perform Excel-type tasks such as sorting, filtering, and aggregation by using Python. 
* **Statistical Analysis and Visualization**   
In this lesson, students will first learn how to perform basic statistical analysis by using the SciPy library, which is similar to the “Analysis ToolPak” in Excel. They will also learn to draw graphs, such as bar charts and scatter plots, by using the Matplotlib library. 
## Day 2:  Data Analysis with Python
**Scope**: Lesson 7–13 from “Python for Business”      
**Contents**:
* **Data Mining Using the CRISP-DM Framework**   
Employing CRISP-DM (cross-industry standard process for data mining) is a popular approach to handle data mining tasks in a regimented manner. Students will first obtain an overview of the CRISP-DM framework. Next, they will explore in more detail one of the more important steps in CRISP-DM – data preparation. For example, skills such imputing missing values, manipulating strings, and lambda function will be introduced to the students. 
* **Data Modeling Process**   
The students will walk through a very basic example of the data analysis process. Steps including loading data, descriptive statistics, building a simple linear regression model, and evaluating the model are presented.
* **Case Study (Titanic)**  
Next, the students will have an opportunity to demonstrate the skills that they have learned. The goal of this case study is to successfully predict which people are most likely to survive the sinking of the Titanic. As part of this project, students will apply CRISP-DM to complete several data analytic challenges on a provided dataset. 
* **Case Study (Chicago Yellow Cab)**   
For their second practicum, the students will complete a longer, more challenging business-related analysis project. The goal in this project is to help the Chicago Yellow Cab Company develop cost saving strategies. The case is broken down into small steps to help students understand data retrieval, data cleaning, model building, and storytelling from a business analytics point of view.  
* **Debugging (Optional)**   
Finding and fixing errors in a program, known as debugging, is an important task. In large part, learning to debug effectively comes from experience. However, in this final lesson, which is optional depending on the target audience’s needs and interests, students will learn several useful debugging tricks that might improve their debugging ability.

# Future work
As a new contribution to the Data Carpentry curriculum, Data Carpentry for Business lessons will continue to be collaboratively refined by an active instructor community supported in part by the University of Illinois Deloitte Foundation Center for Business Analytics.  As the workshop lessons are released, instructor and student feedback will provide an ongoing opportunity for continual improvement and adaptation of the curriculum.  The lesson maintenance team will focus on updating and maintaining the materials to best accommodate student needs.

# Appendix - Workshop Suggested Table of Contents 
|       |             |                     |                                             |
|-------|-------------|---------------------|---------------------------------------------|
| Day 1 |             |                     |                                             |
|       | Time        | Part                | Lesson                                      |
|       | 25 minutes  | SQL for Business    | 01 - Introduction to SQL                    |
|       | 30 minutes  | SQL for Business    | 02 - Getting to know your data              |
|       | 35 minutes  | SQL for Business    | 03 - Basic Queries                          |
|       | 60 minutes  | SQL for Business    | 04 - SQL Aggregation                        |
|       | 50 minutes  | SQL for Business    | 05 - Joins                                  |
|       | 30 minutes  | Python for Business | 01 - Introduction to Jupyter Notebook       |
|       | 30 minutes  | Python for Business | 02 - Intro to Python                        |
|       | 40 minutes  | Python for Business | 03 - Conditional statements and Loops       |
|       | 40 minutes  | Python for Business | 04 - Functions and Modules                  |
|       | 60 minutes  | Python for Business | 05 - Intro to Pandas                        |
|       | 40 minutes  | Python for Business | 06 - Statistical Analysis and Visualization |
|       | 30 minutes  | Python for Business | 07 - (Optional) Errors and Exceptions       |
|       | 30 minutes  | Python for Business | 08 - (Optional) Debugging                   |
| Day 2 |             |                     |                                             |
|       | 30 minutes  | Python for Business | 09 - Introduction to CRISP-DM               |
|       | 60 minutes  | Python for Business | 10 - Data Preparation techniques            |
|       | 60 minutes  | Python for Business | 11 - Linear regression                      |
|       | 30 minutes  | Python for Business | 12 - Case Study 1 - Titanic                 |
|       | 240 minutes | Python for Business | 13 - Case Study 2 - Chicago Yellow Cab      |

# Appendix - Derived contents   
| Our Section                                               | Derived From                                                        | Content Derived                                                                                                      |  
|-------------------------------------------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| SQL Lessons - 1. Introduction to SQL    | SQL for Ecology -  1. Databases using SQL        |  Definitions of concepts are borrowed from SQL for Ecology                                                                                                | 
| SQL Lessons - 2. Getting to know your data    | SQL for Ecology -  1. Databases using SQL  |  Chart of data types in SQL                                                                                                                               | 
| SQL Lessons - 3. Basic Queries    | SQL for Ecology -   2. Basic Queries                   |  Definitions of concepts are borrowed from SQL for Ecology                                                                                                | 
| SQL Lessons - 4. SQL Aggregation    | SQL for Ecology -   3. SQL Aggregation and aliases   |  The structure is inspired from SQL for Ecology (main idea and flow), but we used different examples and descriptions.                                    | 
| SQL Lessons - 5. Joins    | SQL for Ecology -  4. Joins                                    |  The structure is inspired from SQL for Ecology (main idea and flow), but we used different examples and descriptions.                                    | 
| Python Lessons - 7. Extra - Errors and Exceptions     | Python Novice Inflammation - 7. Errors and Exceptions               | Entire section                                                                                                           |   
| Python Lessons - 8. Extra - Debugging                 | Python Novice Inflammation - 9. Debugging                           | Entire section                                                                                                           |  
| Python Lessons - 2. Python basics 1 - Intro to Python | Python for Ecology - 2. Short Introduction to Programming in Python | The structure is inspired from Python for Ecology (main idea and flow), but we used different examples and descriptions. | 
| Python Lessons - 4. Python basics 3 - Functions and Modules | Python Novice Inflammation -  6. Creating Functions | The structure is inspired from Python Novice Inflammation (main idea and flow), but we used different examples and descriptions.   | 

# References
