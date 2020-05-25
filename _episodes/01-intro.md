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

```
(-2 + (2**2-4*1*-3)**0.5)/(2*1)
```

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

You can subsequently change a variable's value by assigning a new value to the same name:

~~~
volume = 50*50*1000
print('volume in liters:', volume/1000)

volume = 80*80*750
print('volume in liters:', volume/1000)
~~~
{: .language-python}


## Organizing Data  

When you work with numbers naturally, you distinguish whole-number counting (1,2,3,4,5,...) from fractional or decimal values (1/3, 3.1415...).  In the same way, it is helpful for computers to distinguish _integers_ (whole-number values) from _floating-point values_ (numbers with a decimal part).

Examples of integers:

    1
    10
    25

Examples of floating-point numbers:

    1.0
    5 / 2
    25 ** 0.5

Note that floating-point numbers and integers, even though they may have the "same" value, aren't the same thing.  We can use the `type` function to ask Python what kind of type a particular value or variable is.

    type(1)
    type(1.0)
    type(5)

You can also write floating-point numbers, or `float`s, using exponential notation:

    1e5

which in this case means 100,000.


> ## Identifying Data Types and Operators
>
> Execute the following statements.  What is the data type resulting from each?  Try to predict the type of the result before you run each line.
>
> 1. `100 * 100`
> 2. `100.0 * 100.0`
> 3. `100 / 10`
> 4. `100 // 10`
> 5. `100 // 7`
> 6. `10 % 7`
>
> > ## Solution
>
> 1. `int` (both inputs are `int`s)
> 2. `float` (both inputs are `float`s)
> 3. `float` (division makes a `float` even if the inputs are `int`s)
> 4. `int` (this is division-without-remainder, or floor-division)
> 5. `int`
> 6. `int` (this is the remainder or modulus function)
> {: .solution}
{: .challenge}

Besides `int` and `float`, there are a couple more basic types:  `bool` and `str`.

#### Booleans (Truth)

`bool` (boolean) results from true/false question, like `4<5` or `6>8`.  You can use greater-than and less-than operators to produce these, or `<=` ($\leq$), `>=` ($\geq$), and `==` (which tests for mathematical equality).

#### Strings (Text)

`str` (string) stores text data.  (Think of characters of text being strung like beads on a string.)

If we need a program to communicate with a user, for instance, we have to distinguish words meant for the computer from words meant for the user.

Thus

    print(Hello world!)

fails, because Python tries to treat `Hello` and `world` as variables.

Instead, you need to wrap the words in quotes to make a string:

    print('Hello world!')

You can use either single quotes `''` or double quotes `""`; just be consistent.

<!-- TODO:exercise : string operations -->
<!-- TODO:exercise : f-strings -->


## Data Containers

#### Lists

When working with data in a spreadsheet, we frequently need to think about the data in a row or in a column.  Since data in a column are frequently treated all the same (like invoice numbers, or transaction amounts), it is convenient to group them together when thinking about calculating.

In Python, we use a `list` for a similar purpose.  We write a list using square brackets `[]`:

```
numbers = [1,2,3,4,5]
data = [67.5,82.0,93.25,102.5,51.0]

print(numbers)
```

Like a spreadsheet, it doesn't have to contain only the same kind of data values, but it is frequently most convenient to work that way.

To access a value inside of a list, you need to use square brackets and an _index_, or a count of where the value is located.

```
print(data[3])
```

(Note that the index counts how many times you move to the right, so it starts at zero to access the first value.  You can also use negative values to count leftwards from the end.)

<!-- TODO:exercise -->

#### Strings Redux

Indexing works for more than just lists, however!  Given a string, you can grab a smaller string containing only part of it.  This also uses square brackets `[]` as an index.

```
text = "Waltz, bad nymph, for quick jigs vex."
```

To grab a single letter, use a single index, just as with a list.

- `text[0]`
- `text[1]`
- `text[12]`
- `text[-1]`

To grab multiple letters, use the starting index and then the final index of the letter you want plus one.

- `text[0:5]` becomes `"Waltz"`, not `"Waltz,"`
- `text[0:-1]` grabs everything _except_ the final character `'.'`.

<!-- TODO:exercise -->

We will work a lot with lists and other containers later on, so for now know how to recognize them when they appear and how to grab out the piece you want.

#### Dictionaries

While counting indices to locate a value works, rather like row numbers in a spreadsheet, it is often convenient to use other data, like a column header, to identify a particular value in a data set.  To that end, we use `dict`, or dictionaries.

Dictionaries attach a label to each value, allowing you to look up the value if you know the label (or "key", in Python's parlance).  We write dictionaries using curly braces `{}`:

```
numbers = {
    'one' : 'i',
    'two' : 'ii',
    'three' : 'iii',
    'four' : 'iv',
    'five' : 'v'
}

print(numbers)
```

Just as you use a numeric index to look up a value in a list, you use the label or key to look up a value from a dictionary:

```
print(numbers['one'])
print(numbers['five'])
```

If a key is not present, what happens?

```
print(numbers['six'])
```

To add a new key, refer to it when you assign the value:

```
numbers['six'] = 'vi'
```

<!-- TODO:exercise -->

## Casting Values

To cast metal is to pour it into a mold, which gives it a new shape.  Similarly, we can "cast" one kind of data into another type, which makes certain calculations easier later on.

It's a bit counterintuitive that an `int` 1 is not the same thing as a `float` 1.0.  The real answer has to do with how they are represented:  the `int` being a number, like a counting number, and the `float` always having a decimal part even if that decimal part is zero.  (This is a major deviation from how spreadsheets handle things—they almost always use `float`s unless counting rows or columns.)

When we use `type` to find out what type a value has, the short answer can be used to convert other types to that type.  In other words, `int(5.0)` converts a `float` to an `int`.

> ## Converting Data Types
>
> Carry out each conversion.  Are there any tricky parts?
>
> 1. `1` to `float`
> 2. `10.0` to `int`
> 3. `10.1` to `int`
> 4. `10.9` to `int`
> 5. `-10` to `float`
> 6. `-10.5` to `int`
> 7. `'10'` to `float`
> 8. `'100%'` to `float`
> 9. `'10.5'` to `int` (this may require two steps)
>
> `round` can also be used to convert numbers, but due to quirks of computer memory it behaves a tad inconsistently.
>
> 10. `round(1.5)`
> 11. `round(0.5)`
> 12. `round(-0.5)`
>
> > ## Solution
>
> 1. `float(1)`
> 2. `int(10)`
> 3. `int(10.1)` (the fractional part is cut off)
> 4. `int(10.9)` (rounding does not occur, just "truncation" or chopping-off)
> 5. `float(-10)`
> 6. `int(-10.5)`
> 7. `float('10')`
> 8. `float('100%')` doesn't work, so you need to grab the part of the number that matters and divide by 100:  `float('100%'[:-1])/100`
> 9. `int(float('10.5'))`
> 10. `round(1.5)` rounds up to 2
> 11. `round(0.5)` rounds _down_ to 0
> 12. `round(-0.5)` rounds _up_ to 0
> {: .solution}
{: .challenge}

A few datatypes are incompatible with each other, or lose information in the transformation:  a dictionary can be converted to a list, but only the keys are preserved.
