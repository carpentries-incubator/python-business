---
title: Python basics 3 - Functions and Modules
teaching: 40
exercises: 0
questions:
- "How can I define new functions?"
- "What's the difference between defining and calling a function?"
- "What happens when I call a function?"
- "What are modules? How could I use pre written functions?"
objectives:
- "Define a function that takes parameters."
- "Return a value from a function."
- "Set default values for function parameters."
- "Explain why we should divide programs into small, single-purpose functions."
- "Import or install modules."
- "Read documentation of modules."
keypoints:
- "Define a function using `def function_name(parameter)`."
- "The body of a function must be indented."
- "Call a function using `function_name(value)`."
- "Numbers are stored as integers or floating-point numbers."
- "Integer division produces the whole part of the answer (not the fractional part)."
- "Variables defined within a function can only be seen and used within the body of the function."
- "If a variable is not defined within the function it is used, Python looks for a definition before the function call"
- "Specify default values for parameters when defining a function using `name=value` in the parameter list."
- "Parameters can be passed by matching based on name, by position, or by omitting them (in which case the default value is used)."
- "Put code whose parameters change frequently in a function, then call it with different parameter values to customize its behavior."
- "import a module with `import` statement. Download a module with `!pip install` statement."
- "For us business students, it is more important to learn what a module can do and how to use the functions in the module than actually implement the functions by ourselves."
---

## Reusing Code

Let's take a break from tabular data for a moment and think about how much code you've written so far.  Most of the code from the exercises has only required small changes from the previous examples you've seen.  In fact, as a rule of thumb, if you ever need to do something on a computer more than twice, you should find a way to make the computer do the job for you.  That is, after all, why we developed them.

If we copy and paste code, there are two problems:

1. Code clarity.  Copying and pasting takes up a lot of room and can be hard to read.
2. Code correctness.  If we make a mistake somewhere, we may have to correct it in many places if we have copied that code around.

Loops are one way of repeating code again and again, but they only work for certain kinds of repetitive processing of a list or data set.

A more general solution is to "wrap up" the useful code as a _function_.  Functions let you reuse the same code again and again, perhaps with slightly different values as you work through the data.

You have already encountered many of Python's [built-in functions](https://docs.python.org/3/library/functions.html), such as `len()`.  You have also loaded functions from a library, such as `statistics.mean`.

On top of these, however, real power is unleashed by creating your own functions.  For instance, this is a new short function which calculates the median of a data set:

```python
def median(data):
    data = sorted(data)
    midpoint = len(data)/2
    if len(data) % 2 == 0:
        # Even data require the central midpoint as the median.
        return (data[int(len(data)/2)-1]+data[int(len(data)/2)])/2
    else:
        # Odd data require simple the middle value.
        return data[int(len(data)/2)]
```

Input this cell into Jupyter and then test it using this code:

```python
values = [1,1,2,2,3,4,4,5,9]
print(f'The median of {values} is {median(values)}.')

values = [1,1,2,2,3,3.5,4,4,5,9]
print(f'The median of {values} is {median(values)}.')
```

A function requires only a `def` statement, a name, and a [body]({{ page.root }}/reference/#function-body).  Most functions also `return` a value.

In an earlier lesson, you wrote code to reverse a string.  Let's wrap that up in a new function.

```python
def reverse(oldstring):
    newstring = ''
    for char in oldstring:
        newstring = char + newstring
    return newstring
```

Notice how much of the code stays the same:  the only real changes are the additions of a header line and a `return` statement.

Every time you write a function, you should test it:

```python
reverse('Stolen Dance')
```

When we _call_ a function, we use the name of the function and we include data for the function inside of the parentheses.  From the function's perspective, the incoming data have the name given them in the function header (which means that the same data may have two names!).

> ## Calculate an Average
>
> Write a function named `average` that returns the average of any given list of numbers.
>
> Hint: use built in functions `sum()` to get the sum and `len()` to get the length
>
> You can test your function using this code (which shouldn't be inside of your function).  It should yield `True`.
>
> ~~~
> data = [1,2,3,4,5,9]
> average(data) == 4.0
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > def average(values):
> >     return sum(values)/len(values)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}


## Libraries Redux

You previously saw libraries (or modules) when we needed to calculate some basic statistics of numbers.  There are many libraries built into Python and many more available from other users.

Now you can see what a module is:  it is a collection of function definitions (and data type definitions, and ...).

### Your Own Library

In fact, any new code that you write can be saved in a `py` file and loaded (from the same directory).  Put the following code into a new plain text file `stats.py` and save it in the same folder that your Jupyter notebook is in.

```python
def median(data):
    data = sorted(data)
    midpoint = len(data)/2
    if len(data) % 2 == 0:
        # Even data require the central midpoint as the median.
        return (data[int(len(data)/2)-1]+data[int(len(data)/2)])/2
    else:
        # Odd data require simple the middle value.
        return data[int(len(data)/2)]

# Include your `average` function as well here.
```

In Jupyter, you can now load and use those functions:

```python
import stats

print(stats.median([-10,-9,100,5,16,85]))
```

### Other Libraries of Note

You've seen `statistics` and `pandas`.  Other libraries which you may need include:

**`math`**.  The `math` module includes helpful basic operations like these:

- `sqrt(x)` for $\sqrt{x}$
- `sin(x)` for $\sin{x}$ (`cos`, `tan`)
- `log10(x)` for $\log_{10} x$, base-10 logarithm
- `exp(x)` for $\exp x$

(Some of these are also duplicated in `pandas` for compatibility with `DataFrame`s and `Series`.)

**`random`**.  Sometimes you need to generate unpredictable values for use with your calculations.

- `uniform(0,1)` for a random floating-point value between 0 and 1 (the bounds can be adjusted)—this is like the chance of probability
- `randint(1,10)` for a random integer between 1 and 8 (the bounds can be adjusted)—this is like rolling a die

Use these functions to create your own business math and data-analytics tools.

> ## Calculating Residuals
>
> A residual is an estimate of the statistical error using actual observed values to calculate.  The set of residuals is calculated for each data point in a set using the mean and the observed value:
>
> $$
> r_{i}
> =
> y_{i} - \bar{y}
> $$
>
> where $r_{i}$ is the $i$-th residual, $y_{i}$ is the $i$-th observation, and $\bar{y}$ is the mean of all observations.
>
> Compose a function `resid` which accepts a list of observations, calculates their mean and the residuals, and returns a list of residuals.
>
> ~~~
> # Starting code
> def resid(values):
>     mean = _____
>     resids = []
>     for i in range(len(values)):
>         resids.append(_____)
>     return resids
> ~~~
> {: .language-python}
>
> You can test your function using this code (which shouldn't be inside of your function).  It should yield `True`.
>
> ~~~
> data = [1.173,1.062,0.807,1.186,1.107,0.897]
> from numpy import isclose  # checks for approximate closeness
> isclose(resid(data),[1.129,1.022,0.777,1.142,1.066,0.864],rtol=1e-3)
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > def resid(values):
> >     mean = sum(values)/len(values)
> >     resids = []
> >     for i in range(len(values)):
> >         resids.append(values[i]/mean)
> >     return resids
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Calculating the Sum of Squared Error (SSE)
>
> The sum of squared error (or residuals) evaluates how much error is present in a model of a data set.  A model $y$ is used alongside actual observations $\hat{y}$.
>
> $$
> \operatorname{SSE}
> =
> \frac{1}{n} \sum_{i=1}^{n} (y_i-\hat{y_i})^{2}
> $$
>
> where $n$ is the total number of observations, $y_{i}$ is the $i$-th observation, and $\hat{y_{i}}$ is the $i$-th model prediction.
>
> Compose a function `sse` which accepts a list of observations and a list of model values and returns the SSE.
>
> ~~~
> # Starting code
> def SSE(obs,fit):
>     n = _____
>     sse = 0  # we start a sum from zero, of course
>     for i in range(n):
>         sse = sse + _____ / _____
>     return sse
> ~~~
> {: .language-python}
>
> You can test your function using this code (which shouldn't be inside of your function).  It should yield `True`.
>
> ~~~
> observed_values = [1.173,1.062,0.807,1.186,1.107,0.897]
> modeled_values = [1.2,1.1,1.0,0.9,0.8,0.7]
> from numpy import isclose  # checks for approximate closeness
> isclose(SSE(observed_values,modeled_values),0.2543,rtol=1e-3)
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > def SSE(obs,fit):
> >     n = len(obs)
> >     sse = 0
> >     for i in range(n):
> >         sse = sse + (obs[i]-fit[i]) ** 2
> >     return sse
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

At this point, although we have been working with lists, I would like you to observe that your code works correctly with numeric fields from `DataFrame`s as well:

~~~
import pandas as pd

data = [['Alex',10,10.3],['Bob',12,11.8],['Clarke',13,13.4]]
df = pd.DataFrame(data,columns=['Name','Age','Age-Actual'])

SSE(df['Age'],df['Age-Actual'])
~~~
{.language-python}

> ## Calculating the Standard Deviation
>
> The sum of squared error (or residuals) evaluates how much error is present in a model of a data set.  A model $y$ is used alongside actual observations $\hat{y}$.
>
> $$
> \sigma
> =
> \sqrt{\frac{1}{n-1}\sum_{i=1}^{n} \left(y_{i} - \bar{y}\right)^2}
> $$
>
> Compose a function `stdev` which accepts a list of observations and returns the standard deviation.  You may wish to use the function `sqrt` from the `math` library.
>
> ~~~
> # Starting code
> def stdev(_____):
>     _____
> ~~~
> {: .language-python}
>
> You can test your function using this code (which shouldn't be inside of your function).  It should yield `True`.
>
> ~~~
> observed_values = [1.173,1.062,0.807,1.186,1.107,0.897]
> from numpy import isclose  # checks for approximate closeness
> isclose(stdev(observed_values),0.1406,rtol=1e-3)
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > def stdev(lt):
> >     average = avg(lt)
> >     sum_squared_dev = 0
> >     for num in lt:
> >         sum_squared_dev = sum_squared_dev + (num - average) ** 2
> >     return math.sqrt(temp/len(lt))
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

As with `stats.py`, you can now save these working functions into a new library module that you can use over and over again.  Copy `resid`, `SSE`, and `stdev` into a new file `stats.py` (or reuse the old one).

~~~
import stats

observed_values = [1.173,1.062,0.807,1.186,1.107,0.897]
from numpy import isclose  # checks for approximate closeness

isclose(stats.stdev(observed_values),0.1406,rtol=1e-3)
~~~
{: .language-python}

Not all modules are included with your Python installation (although we prefer Anaconda because most things are).  Sometimes you have to download the module before importing it.  For example, there is a graphing module called `plotly`.  If you run `import plotly`, it may fail because the library files are not on your computer yet.  You can install it by using the `!pip install` statement:

~~~
!pip install plotly
~~~
{.language-python}

Then you should be able to import the module normally.

You shouldn't need to actually implement your own version of common procedures like the standard deviation.  Pandas, for instance, has it built in:

~~~
df['Age'].std()
~~~
{.language-python}

Elements of your data analysis such as the standard deviation (or even ANOVAs), PCA (dimension reduction), and some probabilistic models are usually available in reputable and well-vetted libraries.  Once you have written part of your analysis, however, moving repeatedly used blocks of code into functions and loops will save you time and effort fairly quickly.

### Writing Readable Functions

Consider the following function:

~~~
def s(p):
    a = avg(p)
    t = 0
    for q in p:
        t = t + (q - a) ** 2
    return math.sqrt(t/len(p))
~~~
{: .language-python}

The functions `s` does calculate the standard deviation, exactly the same as in the previous exercise.  To a human reader, however, it is difficult to read and interpret because of the overly terse variable names and the lack of description.  Using comments to explain complex code and using helpful variable names is a much better approach, since you are the most likely person to have to figure out what your code means later on!

You should also avoid choosing variable names that confuse you when working with a process.  Consider the following example.

> ## Understanding Variable Scope
>
> What does the following piece of code display when run --- and why?
>
> ~~~
> f = 0
> k = 0
>
> def f2k(f):
>   k = ((f-32) * (5.0/9.0)) + 273.15
>   return k
>
> f2k(8)
> f2k(41)
> f2k(32)
>
> print(k)
> ~~~
> {: .language-python}
>
> > ## Solution
> >
> > ~~~
> > 259.81666666666666
> > 287.15
> > 273.15
> > 0
> > ~~~
> > {: .output}
> > `k` is 0 because the `k` inside the function `f2k` doesn't know about the `k` defined outside the function.
> {: .solution}
{: .challenge}

### Using Default Arguments

Many times, it is cumbersome to expect the user to specify _everything_ about a function.  In that case, we can specify a default value to use if the user doesn't give a value for that option.

For instance, you have already seen us use default arguments:

~~~
from numpy import isclose
print(isclose(1,1.01))
print(isclose(1,1.01,rtol=1e-1))
~~~
{: .language-python}

which specifies the relative tolerance (or how close the values have to be before they are considered to be close to each other).

To set these up, define the default value in the function definition:

~~~
def divide_by(a,b=2):
    return a/b

print(divide_by(1))
print(divide_by(1,4))
print(divide_by(1,b=4))  # equivalent but more explicit
~~~
{: .language-python}

> ## Rescale an Array
>
> Write a function `rescale` that takes an array as input and returns a corresponding array of values scaled to lie in the range 0.0 to 1.0.
>
> Hint: If `L` and `H` are the lowest and highest values in the original array,
> then the replacement for a value `v` should be `(v-L) / (H-L)`.
>
> > ## Solution
> > ~~~
> > def rescale(input_array):
> >     L = min(input_array)
> >     H = max(input_array)
> >     output_array = []
> >     for item in input_array:
> >         output_array.append((item - L) / (H - L))
> >     return output_array
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Rescale an Array to a Default Range
>
> Rewrite the `rescale` function so that it scales data to lie between `0.0` and `1.0` by default, but will allow the caller to specify lower and upper bounds if they want.
>
> Compare your implementation to your neighbor's: do the two functions always behave the same way?
>
> > ## Solution
> > ~~~
> > def rescale(input_array, low_val=0.0, high_val=1.0):
> >    L = min(input_array)
> >    H = max(input_array)
> >    output_array = []
> >    for item in input_array:
> >        output_array.append((item - L) / (H - L) * (high_val - low_val)+ low_val)
> >    return output_array
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Readable Code
>
> Revise a function you wrote for one of the previous exercises to try to make the code more readable. Then, collaborate with one of your neighbors to critique each other's functions and discuss how your function implementations could be further improved to make them more readable.
{: .challenge}
