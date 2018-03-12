---
title: Python basics 1 - Intro to Python
teaching: 20
exercises: 0
questions:
- "What is Python?"
- "What are variables?"
objectives:
- "Assign values to variables."
- "Select individual values and subsections from data."
- "Convert datatypes"
keypoints:
- "Use `variable = value` to assign a value to a variable in order to record it in memory."
- "Variables are created on demand whenever a value is assigned to them."
- "Use `print(something)` to display the value of `something`."
---

## What is Python?
[Python](https://www.python.org/doc/essays/blurb/) is an interpreted, object-oriented, high-level programming language with dynamic semantics. Its high-level built in data structures, combined with dynamic typing and dynamic binding, make it very attractive for Rapid Application Development, as well as for use as a scripting or glue language to connect existing components together. Python's simple, easy to learn syntax emphasizes readability and therefore reduces the cost of program maintenance. Python supports modules and packages, which encourages program modularity and code reuse. -- python.org

## Why learning Python as a business student?  

## Variables 

Lets start by learning about variables. A variable is a name for a value, you can name it whatever you want. 
Python's variables must begin with a letter and are case sensitive.
We can create a new variable by assigning a value to it using `=`.
When we are finished typing and press Shift+Enter,
the notebook runs our command.

This is how you assign a value to a variable:  

```
a = 1
```
Ok, now you have successfully assigned value 1 to a variable called `a`.  
To see the value in the variable, we can simply do:  
```
a
```
or 
```
print(a)
```

## Datatypes  
Datatype is to classify the value of variables. 
In the previous example, you assigned a numerical value to a variable. 
Here are some common built in datatypes. Thare are a lot of built in datatypes, you can check [here](https://docs.python.org/3/library/stdtypes.html) for details.  
 
#### 1. Boolean 
`boolean` has only two possible values: True or False. 

#### 2. Numerical 
- `int`: integers, such as 1, 2, 3 ...   
- `float`: numbers with digits, such as 1.1, 2.23, 3.14159, etc. 

#### 3. Strings
- `str`: similar as texts, such as "a", "nyan nyan nyan", "oppa gangnam style" 
- Note that, if you add quotation marks to a numerical data, it will become a string. For example, "1" is a string. 

#### 3. Sequence types  
- `tuple`: immutable finite ordered list, put in parentheses. For example, `(1,2,3)`, `("a","a","b")`, `(("a",1,3),"b",3)`. It's just like a container, you can put various kinds of data in it.  
Let's create a tuple
```
tp = (1,2,3) 
```
To get a single value from the tuple, we can do:  
```
tp[0]
```
- `list`: mutable finite ordered list, put in square brackets. For example, `[1,2,3]`, `["a","a","b"]`, `[("a",1,3),"b",3]`. 
Let's create a list 
```
lt = [1,2,2,3]
```
To get a single value from the list, we can do:  
```
lt[0]
```
To add a value into a list, we do: 
```
lt.append(5)
```
You can also append a list to a list.  
Well, what's the difference between tuple and list? Tuple is immutable, that means, you cannot change the stuff in the tuple
```
tp[0] = 3
```
The above code will create an error. But for lists, you can:  
```
lt[0] = 3
```
lets see if the item in the list changed: 
```
print(lt)
```
- `set`: unordered collection with no duplicates. 
To create a set, you do:  
```
st = set([1,2,2,3]) 
print(st)
```
Only one "2" is left. You can also do `st = set((1,2,3))` or `st = set(tp)`, basically you are converting a list or a tuple into a set. `set()` is great way to remove duplicates or perform set operations (recall from high school algebra). 

#### 4. Dictionary
- `dict`: unordered {key: value} pairs, indexed by keys. Keys cannot be mutable, so tuples can be keys but lists cannot be keys. It sounds confusing, lets see an example:  
```
dt = {"a":1, "b", 2}
```
In this dictionary dt, "a" and "b" are keys, 1 and 2 are values. Keys are unique, so you can quickly get the value behind the key by:
```
dt["a"]
```
To add a {key: value} pair to a dictionary, you do:  
```
dt["c"] = 3
```
or
```
dt.update({"c" : 3})
```
If the key already exists in the dictionary, it will not duplicate a key. Instead, it will update the value behind the key.  

#### checking datatypes  
To check the datatype of a variable, we can use `type()` function: 
```
type(dt)
```

#### changing datatypes
You actually have done this previously. You have successfully converted a list to a set. To change datatypes, we can do `desired_datatype(variable)`. For example, we can convert the dictionary dt to string by: 
```
str(dy)
```
You can convert a float to an interger by: 
```
int(1.7)
```
Note that, int() **always round down**, so you will get 1 if you do `int(1.7)`

However, this would not always work. Some datatypes are not interchangable. For example, you cannot convert a dictionary to a integer by `int(dt)`. It is kind of intuitive, an integer is a single number, but a dictionary is {key : value} pairs. 

## Arithmetics 
You can get output from python by typing math into the console:
```
3+5
2*7
```
and do arithmetic with variables:

~~~
volume = 750 * 6
print('volume in litter:', volume/1000)
~~~
{: .language-python}

As the example above shows,
we can print several things at once by separating them with commas.

We can also change a variable's value by assigning it a new one:

~~~
volume = 750 * 6
print('volume in litter now:', volume/1000)
~~~
{: .language-python}

While a lot of powerful, general tools are built into languages like Python,
specialized tools built up from these basic units live in [libraries]({{ page.root }}/reference/#library)
that can be called upon when needed.


