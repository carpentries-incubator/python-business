---
title: Statistical Analysis and Visualization
teaching: 40
exercises: 0
questions:
- "How can I perform statistical analysis in Python?"
- "How to visualize my data"
objectives:
- "Learn to perform statistical analysis with Scipy.stats module"
- "Learn to visualize data with matplotlib"
keypoints:
- "Use `scipy.stats.ttest_ind` for t-test"
- "There are many other statistical tools in scipy, you can read the documentation for more details"
- "You can customize many parameters in your graph, you can read the documentation for more details"
- "For both Scipy and matplotlib, the most difficult part is to preprocess your data. After that, you can just find the right function and feed your data into it."
---

## Statistical Analysis

Similar as the Dada Analytics Tools in Excel, python can perform many statistic analysis as well. [`scipy`](https://www.scipy.org/) module has many useful statistic tools. (more than Excel).

### t-test
Assume you are interested in selling either energy drink or cola, and you want to know if the two categories has significant difference in average bottle sales.
We can perform a [t-test](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_ind.html) assuming different variance.
Firstly we need to import the stats module.
```python
from scipy import stats
```
Then we need to use aggregate function to find the total bottle sold for each soda in each category. Remember the groupby function? Try to do it by yourself.

```python
ct = inv_soda.groupby(['Item_Description','Category'], as_index=False).agg({"Bottles_Sold":"sum"})
```

Then, you get the total bottles sold for the two categories.
```
ct_eng = ct[ct["Category"] == "Energy Drink"]
ct_cola = ct[ct["Category"] == "Cola"]
```
Finally, you perform the t-test.
```
stats.ttest_ind(ct_eng['Bottles_Sold'],ct_cola['Bottles_Sold'], equal_var=False)
```
Then you get
```
Ttest_indResult(statistic=1.9035249229837687, pvalue=0.057480903679786859)
```
{: .output}
Well, the p value is not low enough to reject the null.  <br>

#### Takeaways
* Scipy has a lot of statistical tools. You can perform anything in the Excel Data Analytics Tool with Scipy, yet it is much more powerful. For example, you can do [chi-squares](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.chisquare.html#scipy.stats.chisquare), [ANOVA](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.f_oneway.html#scipy.stats.f_oneway), [k-stat](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.kstat.html#scipy.stats.kstat), etc. You can click the link to see all tools in [Scipy.stats](https://docs.scipy.org/doc/scipy/reference/stats.html).
* As you can observe above, the most difficult part is to preprocess the data. As soon as the data is prepaired, you can just feed it into the model, very easy.
* There are many modules that can perform stats tasks in python. For example, [sklearn](http://scikit-learn.org/stable/), [Statsmodles](https://www.statsmodels.org/stable/index.html) are also great. You can play with those if you have time.

## Visualization

### Basics
Many of you are experts in Excel graphing. You can do similar visualization with python. [`matplotlib`](https://matplotlib.org/) is a good starter module for visualization in python. Firstly, let's import the module.

```python
%matplotlib inline
# In majority of cases, you will just use pyplot. So you can just import that.
import matplotlib.pyplot as plt
```
Similar as Excel, you just need to feed in the values in x-axis and y-axis. Let's start with a very basic example:
```python
# create three points for the first line
x = [1,2,3]
y = [2,3,5]
# create three points for the second line (optional, I just want to show you that you can plot multiple lines in one graph)
x2 = [1.5,2.5,3.5]
y2 = [2.7,3.7,5.7]
# change size (set size before plotting)
plt.figure(figsize=(10,7))
# plot the graph
plt.plot(x,y, label = "first line")
plt.plot(x2,y2, label = "second line")
# Set x, y limits
plt.xlim(0, 5)
plt.ylim(0, 7)
# Add x, y label
plt.xlabel("independent variable")
plt.ylabel("dependent variable")
# Add title
plt.title("example")
# Add legend
plt.legend()
# show the graph
plt.show()
```
You will get something like this:
![graph](../pic/graph.png){:height="400px"}

Without a graphic interface like Excel, it is a little less intuitive. Carefully review the code, and try to understand what each line is doing.  Note that [`pyplot.plot`](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.plot.html) (you can click to read the documentation) has a lot of parameters. Basically, you can customize everything such as color, marker, alpha, etc.

### Histogram
Let's go back to our data.
Assume you want to see the price distribution of the soda that cost less than $5, you can draw a histogram with [`pyplot.hist`](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist.html).

```python
# set size
plt.figure(figsize=(10,7))
# feed in the data, set range, plot the graph
plt.hist(soda['Bottle_Cost'], range=(0,5))
# set x, y label
plt.xlabel("price")
plt.ylabel("number of soda")
# Add title
plt.title("Price distribution")
plt.show()
```
![hist](../pic/hist.png){:height="400px"}

This is a very basic example. You can customize a lot more parameters such as colors, bins, etc.

### Scatter plot

A scatter plot is a two-dimensional data visualization that uses dots to represent the values obtained for two different variables.

```python
# set figure size
fig, ax = plt.subplots(figsize=(10,7))
# Plot data
ax.scatter(soda['Bottle_Cost'], soda['Bottle_Retail_Price'])
plt.xlabel("Bottle_Cost")
plt.ylabel("Bottle_Retail_Price")
# Set title
plt.title("Bottle_Retail_Price VS Bottle_Cost")
# Set x, y limit
plt.xlim(1, 5)
plt.ylim(1, 10)
plt.legend()
plt.show()
```
![sc](../pic/sc.png){:height="400px"}

#### Takeaways
* You can do many other kinds of visualizations with matplotlib. For example, [pie chart](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.pie.html), [bar chart](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.bar.html), etc.
* Anything you can draw in Excel, you can do it with matplotlib. Similar as statistical analysis, the most difficult part for visualization is preprocessing. After that, you can just feed your data into the pre-written graphing tool.
* If you are going to big companies, you will probablly learn Tableau later. Tableau can easily create nice graphs but it is a little annoying in preprocessing. We can preprocess with python and feed the data to Tableau. <br>
* Last but not the least, there are many other cool visualization modules avaliable. If you have time, you can consider these modules: [plotly](https://plot.ly/), [graph-tool](https://graph-tool.skewed.de). They can draw cool and interactive graphs.

> ## Challenge
> Assume you just opened a new convenience store. You want to see what categories of soda did other stores spend the most money on in their inventory.
> What are the top three categories in terms of total cost? Visualize it with pie chart. Read the [documentation](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.pie.html) yourself and try to figure out how to draw it.
> Hint: 1. Calculate total cost for each soda (arithmetic)
> 2. Calculate total cost for each category (aggregation)
> 3. Sort the aggregated value
> 4. draw the graph (what is the x? what is the label?)
> 5. set autopct parameter to '%.0f%%'
>
>> ## Solution
>>
>> ```
>> inv_soda["Total_Cost"] = inv_soda["Bottle_Cost"] * inv_soda["Bottles_Sold"]
>> ct = inv_soda.groupby(['Category'])["Total_Cost"].agg(["sum"]).reset_index()
>> ct = temp.sort_values("sum", ascending = False)
>> plt.figure(figsize=(15,15))
>> plt.pie(ct["sum"], labels=ct["Category"], autopct='%.0f%%')
>> plt.show()
>>
>> ```
> {: .solution}
{: .challenge}
