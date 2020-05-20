---
title: Introduction to Python
teaching: 30
exercises: 15
questions:
- "What is a program and why do we write programs?"
- "What is Python?"
- "How are variables used in programming?"
- "What are the basic data types and containers used in Python?"
objectives:
- "Enumerate six benefits of writing programs to analyze data."
- "Employ variables to name and hold values for subsequent use."
- "Distinguish basic data types one from another."
- "Convert values from one data type to another."
- "Select individual values and subsections from data using indexing and slicing."
keypoints:
- "Use `variable = value` to assign a value to a variable in order to record it in memory."
- "Variables are created on demand whenever a value is assigned to them."
- "Use `print(something)` to display the value of `something`."
---

## What is a program?

To begin, what do we mean by programming?  A computer program is a set of instructions that define a procedure, but that's a rather dry way of saying it.  

At the highest level of understanding, a programming language is a way of writing down a set of steps to consistently produce a particular result.  (Think of a "program" as in a play, or the stage directions.)  At the lowest level, it's a way of moving and changing values in memory.  Whenever you carry out a task on a computer, particularly an involved one like data analysis, you should carefully record the process as a program.  This has the following benefits:

1.  The program makes the process _repeatable_.
2.  The program can remove human error by making the process _automatic_.
3.  The program can be tested (_testable_) and corrected if errors are found.
4.  The program can be shared with others (_sharable_).

These four characteristics—repeatability, automation, testing, and sharing—will be emphasized throughout these lessons.


## What is Python?

When you write a program, you have many choices of programming languages available.  A language is a particular way of writing down the steps of your analysis, and like human languages they offer different benefits and costs.  We will introduce Python in this workshop because it embodies the four characteristics we just introduced and because it is considered fairly readable.  The most valuable language is the one that you can understand, particularly as your analyses become more sophisticated, so don't hesitate to ask questions about every aspect as we delve into Python.

Python prefers English-language words and statements that are reasonably close to mathematics as you have seen previously.  Many programmers like it because it can be written quickly, it works well with many other languages, and it is highly portable.  For you, this means that code you write using Python can be shared with others and run on either Windows or macOS.  Python's popularity has led to a positive feedback loop in which many new code libraries and analysis programs have been published using it.

There are a couple more reasons to employ programming that are worth mentioning, specific to your business studies:

5.  An automatic, repeatable program is more _efficient_; in the end, it will extend your ability to complete analysis more rapidly once your programs are written.
6.  Python is more _scalable_ than many graphical programs, such as Excel.  Spreadsheets have built-in limits on the number of rows and columns which can be reached when processing transactions or event records; Python has only the limits of computer memory.

All together, we hope that you find the benefits of repeatability, automation, testing, sharing, efficiency, and scaling to far outweigh the initial investment you'll make in learning Python-based analysis.


## Your First Python Program

Open the Jupyter notebook dashboard.  We should complete all of our work for a given project in the same directory, so go ahead and use the `New` button to create a new folder on your Desktop named `dcb` (for Data Carpentry for Business).  Click into that folder and start a new Python notebook.  Name it `Lesson 1` and save it immediately.

When we wrote code earlier as short mathematical statements, we were able to express basic arithmetic and algebraic relationships.  For instance, try the following:

    (-2 + (2**2-4*1*-3)**0.5)/(2*1)

Does this look familiar?  This is an expression for the quadratic equation,

$$
x
=
\frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$

with $a=1$, $b=2$, and $c=-3$.  It's a bit inconvenient though:  to change the expression to use the values $a=2$, $b=6$, and $c=-4$ requires changing a number of values manually.  (Take a moment to do it, so you can see the tedium.)

If we are relying on the computer to automate our tasks, then surely there must be an easier way.  Just as we use markers when we refer to the mathematical statement

$$
x
=
\frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$

with $a$, $b$, and $c$, we can set the same values in Python.  In Python, we call such values _variables_.  One implementation looks like this:

    a = 1
    b = 2
    c = -3
    x = (-b + (b**2-4*a*c)**0.5)/(2*a)

Since it doesn't show us the output anymore, we need to prompt Python to show us the result.  Add the following line to the end of the cell and run it again:

    print(x)

Take a moment and copy this to a new cell altogether and execute it.

Next, copy the entire block of code to a new Jupyter cell and change the values to $a=2$, $b=6$, and $c=-4$.  The relative ease and clarity of variables makes their use more straightforward than mucking around directly inside of expressions.

Any time you see a `=` used by itself, it takes whatever the result is on the right and assigns it to the name on the left.  This means that some expressions which are mathematically valid may require alteration to work in Python.

For instance, this fails:

    x - 2 = 4

while this works:

    x = 4 + 2

Keep your basic algebra in mind so you can get a single value on the left-hand side.

> ## Writing Expression with Variables
>
> Consider the equation for an amortized loan payment:
>
> $$
> I
> =
> P\,r\,t
> $$
>
> Write some Python code which implements this equation using variable names and the arithmetic operator `*` for multiplication.  You may use the values $P=1,000$, $r=5\%$, and $n=12$.
>
> > ## Solution
> ~~~
> P = 1000
> r = 0.05
> t = 12
> R = P*r*t
>
> ~~~
> {: .language-python}
>
> You'll notice that writing expressions including commas to separate thousands or percentage signs to represent percents don't work quite the way you may expect.  Python in general expects you to write numbers in a very consistent format—it's rather the sort of pedantry you'll have to get used to.  Most programming languages have quite strict rules regarding how to write numbers and other values.
> {: .solution}
{: .challenge}

> ## Writing Complicated Expressions
>
> Consider the equation for an amortized loan payment:
>
> $$
> R
> =
> \frac{P\,i}{1-(1+i)^{-n}}
> $$
>
> Write some Python code which implements this equation using variable names and the arithmetic operators `+`, `-`, `*`, `/`, and `**`.  Parentheses can organize your terms.  You may use the values $P=1000$, $i=0.034$, and $n=60$.
>
> > ## Solution
> ~~~
> P = 1000
> i = 0.034
> n = 60
> R = (P*i) / (1-(1+i)**-n)
>
> ~~~
> {: .language-python}
> {: .solution}
{: .challenge}

<!-- TODO -->

## Datatypes  
Datatype is to classify the value of variables.
In the previous example, you assigned a numerical value to a variable.
There are a lot of built in datatypes, you can check [here](https://docs.python.org/3/library/stdtypes.html) for details.  
Lets briefly review some common built in datatypes.

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
dt = {"a":1, "b":2}
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
str(dt)
```
You can convert a float to an integer by:
```
int(1.7)
```
Note that, int() **always rounds down**, so you will get 1 if you do `int(1.7)`

However, this would not always work. Some datatypes are not interchangeable. For example, you cannot convert a dictionary to a integer by `int(dt)`. It is kind of intuitive, an integer is a single number, but a dictionary is {key : value} pairs.

## Arithmetics
You can get output from python by typing math into the console:
```
3 + 5
2 * 7
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
volume = 250 * 6
print('volume in litter now:', volume/1000)
~~~
{: .language-python}
