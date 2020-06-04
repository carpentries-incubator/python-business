---
title: Working with Tabular Data
teaching: 60
exercises: 0
questions:
- "How do I read a file"
- "What is pandas"
- "How to work with table-like data in Python like Excel"
objectives:  
- "Describe what the Python Data Analysis Library (Pandas) is."
- "Load the Python Data Analysis Library (Pandas)."
- "What's in our data?"
- "Describe what a DataFrame is in Python."
- "Access and summarize data stored in a DataFrame."
- "Merge two dataframes, understand different types of join  "
- "Perform basic mathematical operations and summary statistics on data in a Pandas DataFrame."
- "Create pivot table"
keypoints:
- "Use `read_csv` to read tabular data into Python."
- "use sort_values([columns]) to sort the dataframe."
- "use df_object.column_name or df_object[column_name] to select one column."
- "use df_object[list_of_column_names] to select multiple columns."
- "use df_object[condition] to filter data. For example, df_object[df_object[column_name] == value]."  
- "use .describe() to get descriptive statistics of one column."    
- "use df1.merge(df2) to merge two DataFrames."  
- "use df_object.groupby(column_list1).agg({column1:agg_function1, column2:agg_function2...}) to apply aggregation on data group."
- "Create pivot table with pandas.pivot_table"  
---


## Merge database  

Sometimes we need data from many different tables.
For example, we have two tables below:  
![vlookup1](../pic/vlookup1.png){:height="130px"} <br>
And we want to merge them together: <br>
![vlookup1](../pic/vlookup2.png){:height="130px"} <br>
Many people probably know how to do this in Excel. You can just use vlookup function. (you will probably use it a lot in your future jobs)
```Excel
=VLOOKUP(A3,$E$3:$F$5,2,FALSE)  
```
We can also do this in Pandas with [`pandas.DataFrame.merge`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.merge.html) (you can click to see documentation).  
```python
# I only listed some frequently used parameters. You can see all parameters in the documentation.  
DataFrame.merge(Another_DataFrame, how='inner, outer, left or right', left_on="Left_Join_Column_Name", right_on="Right_Join_Column_Name")
```
"how" determines the join type. The following chart shows the difference between each kinds of joins, assume column "J" is the join column:  
![join](../pic/join.png){:height="400px"} <br>

Let's have a quick demonstration of the merges performed in the charts above.
```python  
# firstly, load in the tables
table1 = pd.DataFrame({'J': ['A', 'B', 'D'], 'X': [1, 2, 3]})
table2 = pd.DataFrame({'J': ['B', 'C', 'D'], 'Y': [4, 5, 6]})
```
```python
# inner join
table1.merge(table2, how="inner", right_on="J", left_on="J")
# outer join
table1.merge(table2, how="outer", right_on="J", left_on="J")
# left join
table1.merge(table2, how="left", right_on="J", left_on="J")
# right join
table1.merge(table2, how="right", right_on="J", left_on="J")
```

Let's go back to our data. We have two DataFrames, `soda` and `invoice`. In the `invoice` DataFrame, the only information about soda is the "Item_id" column. If we want to see details of the soda associated with each invoice, we need to join the two tables together. Since `soda` DataFrame also has "Item_id" column, "Item_id" column can be used as join column.   
> ## Challenge
>
> Merge `soda` and `inv` tables, call it **inv_soda**.
> Not all kinds of soda will appear in the invoice (some were never sold). If we want to keep everything in the `soda` dataframe, what kinds of join should we use?
>
>> ## Solution
>> ```
>> inv_soda = inv.merge(soda, how="left", right_on="Item_id", left_on="Item_id")  
>> ```
>>  
> {: .solution}
{: .challenge}

> ## Challenge
>
> Check how many rows are there in the joined table. Is it the same as the invoice table (930508 rows)?  
> If they are different, find the exact problem child/children that caused the difference.  
> Hint: to find which value is empty, you can do `df[df["column_name"].isnull()]`  
>
>> ## Solution
>> ```python
>> len(inv_soda)
>> ```
>> The result is 93509 rows. This is because one kind of soda was never sold.  
>> Let's find out what is it:  
>> ```
>> inv_soda[inv_soda["Invoice_id"].isnull()]  
>> ```
>> Yummy Surstromming Juice. Try it, its good.    
>>
> {: .solution}
{: .challenge}

## Aggregate Function  

But if we want to summarize by one or more variables, for example, if we want to find out how many bottles has each soda been sold.
In Excel, we will probably use pivot table. In Pandas, we can use **Pandas' `.groupby` method**. Once we've created a groupby DataFrame, we
can quickly calculate summary statistics by a group of our choice. <br>   
Note that Pandas has pivot table too, we will cover later.   

```python
# Group data by Item_Description
# The code below counts the number of invoice_id associated with each Item_Description. You can have other
grouped_df = inv_soda.groupby('Item_Description').agg({"Invoice_id":"count"})
grouped_df
```
You will get something like this:
```
                      Invoice_id
Item_Description  
Ace's Energy          262
Ace's Energy Booster  64
Akame's Energy        80
...
```
Note that "Item_Description" and "Invoice_id" are not at the same level. This is because the groupby function automatically made "Item_Description" the index. If we do `grouped_df.columns`, we will only see the `Invoice_id` column. To avoid problems when using the aggregated result, we might want to:
```python
grouped_df = inv_soda.groupby('Item_Description', as_index=False).agg({"Invoice_id":"count"})  
grouped_df  
```
The columns are at the same level now.
```
  Item_Description        Invoice_id
0 Ace's Energy            262
1 Ace's Energy Booster    64
2 Akame's Energy          80
...
```
Now if you do `grouped_df.columns`, both "Item_Description" and "Invoice_id" will show up.  

The column of count has the name of the counted column, or Invoice_id. You may change it to a more descriptive name with `rename()` function.  

```python
inv_soda.groupby('Item_Description', as_index=False).agg({'Invoice_id':'count'}).rename(columns={'Invoice_id':'Count'})
```
The output now is:
```
  Item_Description        Count
0 Ace's Energy            262
1 Ace's Energy Booster    64
2 Akame's Energy          80
...
```

Note that the input in `.agg()` is a dictionary. Because we can generate multiple aggregate columns at the same time. For example:  

```python
inv_soda.groupby('Item_Description', as_index=False).agg({"Invoice_id":"count", "Bottle_Cost":"mean"})
# think about this, what does it return?   
```

> ## Challenge
>
> Find the average `Bottle_Cost` and `Bottle_Retail_Price` for each category
>
>> ## Solution
>>
>> ```
>> inv_soda.groupby('Category', as_index=False).agg({"Bottle_Cost":"mean","Bottle_Retail_Price":"mean"})
>>
>> ```
> {: .solution}
{: .challenge}

## Pivot Table  
One of the most useful functionalities in Excel is pivot table. You can also create [pivot table](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.pivot_table.html#pandas-pivot-table) with Pandas!

A basic pivot table contains the following parameters:  
```python
pandas.pivot_table(DataFrame, values, index, columns, aggfunc)
# values: columns to aggregate (just like choosing the field to report in Excel pivot table)
# index: keys to group by on the pivot table index (just like dragging into the row box in Excel pivot table)
# columns: keys to group by on the pivot table column (just like dragging into the column box in Excel pivot table)
# aggfunc: aggregate function, for example, mean, sum, min, etc. (just like setting the values box in Excel pivot table)
```
For example you want to see the total bottles sold for each soda in each city, you can:  
```
pd.pivot_table(inv_soda, values="Bottles_Sold", index = ["Item_Description"],\
            columns = ["City_Name"], aggfunc="sum")   

```
You will get something like this:  
![pt](../pic/pivot.png){:height="300px"}

> ## Challenge
>
> Create a pivot table that shows the total bottle sold for from each vendor in each category. Set Vendor_Name as index and Category as columns.
>
>> ## Solution
>>
>> ```
>> pd.pivot_table(inv_soda, values="Bottles_Sold", index = ["Vendor_Name"],\
            columns = ["Category"], aggfunc="sum")
>>
>> ```
> {: .solution}
{: .challenge}
