---
title: Controlling Program Behavior
teaching: 60
exercises: 30
questions:
- "How can my programs do different things based on data values?"
- "How can I do the same operations on many different values?"
objectives:
- "Write conditional statements including `if`, `elif`, and `else` branches."
- "Correctly evaluate expressions containing `and` and `or`."
- "Explain what a `for` loop does."
- "Correctly write `for` loops to repeat simple calculations."
- "Trace changes to a loop variable as the loop runs."
- "Trace changes to other variables as they are updated by a `for` loop."
- "Use libraries to access pre-written and pre-vetted code."
keypoints:
- "Use `if condition` to start a conditional statement, `elif condition` to provide additional tests, and `else` to provide a default."
- "The bodies of the branches of conditional statements must be indented."
- "Use `==` to test for equality."
- "`X and Y` is only true if both `X` and `Y` are true."
- "`X or Y` is true if either `X` or `Y`, or both, are true."
- "`True` and `False` represent truth values."
- "Use `for variable in sequence` to process the elements of a sequence one at a time."
- "The body of a `for` loop must be indented."
- "Use `len(thing)` to determine the length of something that contains other values."
---

## Conditional Statements

Any useful program will need to make decisions on the basis of incoming data.  Sometimes data need to be thrown out, or converted to a new format, or used to look up other values, or sent to a different database:  hundreds of cases for decisions exist.  More than that, if we are emphasizing making a process automatic, then clearly we need the program to produce different outputs for different conditions without needing our intervention.

Right now, what is the only way we have to distinguish true statements from false statements?  The boolean value, `True` or `False`, lets the program ask a question.  Based on that result, the program can take one of two different paths.  We call this a _conditional statement_ because it changes based on the conditions evaluated using the boolean `True`/`False`.

One simple conditional program takes a calculation, asks a question about it, and prints one of two different statements.

~~~
result =

if result > 0:
    print('The result is positive.')
else:
    print('The result is not positive.')
~~~
{: .language-python}

Notice the parts of this statement:

- `if` initiates the conditional statement.
- `return > 0` is a boolean expression, yielding `True` or `False`.
- The colon `:` indicates that a _block_ of code will start on the next line.
- The indented `print` statement is the first _branch_ or option in the program, evaluated only if the boolean is `True`.
- `else` indicates the alternative option.
- The second indented `print` statement is the other branch in the program.

Only one of these two `print` statements can possibly be run, but one of them _will_ run (if an error does not occur).

Anything that is indented after a colon `:` is considered part of a block.  (We will write programs that have other kinds of blocks as well.)

<!-- TODO:exercise : conditionals -->

<!-- TODO:exercise : indentation correction -->

<!-- TODO:exercise : nested indentation -->

```
a = 1
b = 3
if (a == 1):
    print("a is one!")
    if (b == 2):
        print ("b is two!")
```

Sometimes our truth conditions are more complicated:  we may want to find all transactions which took place between 6 a.m. and midnight at all stores south of Highway 27.  Logical tests can be combined using `and` (which requires both sides to be true) and `or` (which requires only one side to be true).

<!-- TODO examples -->


> ## Challenge 1.1
>

> Consider this code:
>
> ~~~
> if 4 > 5:
>     print('A')
> elif 4 == 5:   # TODO FIXME no more elif
>     print('B')
> elif 4 < 5:
>     print('C')
> ~~~
> {: .language-python}
>
> Which of the following would be printed if you were to run this code?
> Why did you pick this answer?
>
> 1.  A
> 2.  B
> 3.  C
> 4.  B and C
>
> > ## Solution
> > C gets printed because the first two conditions, `4 > 5` and `4 == 5`, are not true,
> > but `4 < 5` is true.
> {: .solution}
{: .challenge}


## Loops

We have promised again and again that we can make programs automatic and efficient.  Part of that solution is to design programs that do drudgery for you, rather than you having to tediously alter and re-run small bits of code.

Now, we can't promise that all the elbow grease will go away, but once you have a process that works the way you want, a _loop_ can make the computer repeat a working process over and over again on new data.  A spreadsheet can help you process 100,000 rows of data:  a Python program can help you process 100 million.

Consider a single-step process, which takes the first element from a list and prints it.

~~~
assertions = ["Existence","Rights and Obligations","Completeness"]

print(f'One account balance assertion when accounting is {assertions[0]}.')
~~~
{: .language-python}

To repeat this process becomes tedious:

~~~
assertions = ["Existence","Rights and Obligations","Completeness"]

print(f'One account balance assertion when accounting is {assertions[0]}.')
print(f'One account balance assertion when accounting is {assertions[1]}.')
print(f'One account balance assertion when accounting is {assertions[2]}.')
~~~
{: .language-python}

Now what happens when you need to add another value to the list?
~~~
assertions = ["Existence","Rights and Obligations","Completeness","Valuation and Allocation"]
~~~
{: .language-python}

To print all four, you need to go back and actually change your program!  And with loaded data (as from a file or a website), where you don't know the size in advance, this approach simply won't work.  (Imagine doing this for hundreds or thousands of entries!)

The better way is to produce a loop, which runs once for each thing in the list:

~~~
assertions = ["Existence","Rights and Obligations","Completeness","Valuation and Allocation"]

for assertion in assertions:
    print(f'One account balance assertion when accounting is {assertion}.')
~~~
{: .language-python}

This program is completely flexible.  Change the number of values in the list `assertions` and the program adapts to deal with each of them in turn.  (We call this kind of loop a [`for` loop]({{ page.root }}/reference/#for-loop)—there are others but we won't worry about them here..)

When processing data in a spreadsheet, one frequently adds a column, writes a formula relating the values in the previous columns, and then copies the formula down through all of the cells.  That's like our first approach:  specific to a set of data and the number of rows therein.  Our second approach, the `for` loop, is more general, because it says, "for each row in the database, carry out this operation."

In general, when you need to carry out the same processing for more than one data value, a `for` loop is a good option.

> ## Building a `for` Loop:  Printing Any Values
>
> Given a set of transaction-level assertions, write a program with a `for` loop to print each one with an explanatory message.
>
> ~~~
> transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
> ~~~
> > ## Solution
> > ~~~
> > transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
> >
> > for transaction_assertion in transaction_assertions:
> >    print(f'One account balance assertion when accounting is {transaction_assertion}.')
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Building a `for` Loop, Part 2:  Counting Objects
>
> Given a set of transaction-level assertions, write a program with a `for` loop to print a sequential number for each one.
>
> In order to do this, it may be helpful to know that you can write a `range` expression, which fills in a set of numbers.  Start with this code:
>
> ~~~
> transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
>
> for index in range(length(transaction_assertions)):
>     print(_____)
> ~~~
> > ## Solution
> > ~~~
> > transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
> >
> > for index in range(length(transaction_assertions)):
> >    print(f'The {index}th account balance assertion when accounting is {transaction_assertions[index]}.')
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Building a `for` Loop, Part 3:  Putting It Together
>
> Given a set of transaction-level assertions, write a program with a `for` loop to print each one preceded by its number.
>
> In order to do this, it may be helpful to know that you can write a `range` expression, which fills in a set of numbers.  Start with this code:
>
> ~~~
> transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
>
> for index in range(length(transaction_assertions)):
>     print(_____)
> ~~~
> > ## Solution
> > ~~~
> > transaction_assertions = ["Accuracy", "Classification", "Completeness", "Cutoff", "Occurrence"]
> >
> > for index in range(length(transaction_assertions)):
> >    print(f'The {index}th account balance assertion when accounting is {transaction_assertions[index]}.')
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

Keep in mind the following principles when working with a `for` loop:

1. Every loop has a `for`, a loop variable through a container, a colon `:`, and a body.
2. The container may be a list, a string, or a dictionary, but is very commonly a list.
3. The body will repeat once for each item in the list.

> ## What's in a name?
>
> In the foregoing example, the loop variable was given the name `assertion` because it related to the list `assertions`.  This isn't constrained:  you can choose any valid Python name for the loop variable.
>
> ~~~
> assertions = ["Existence","Rights and Obligations","Completeness","Valuation and Allocation"]
> for thing in assertions:
>     print(thing)
> ~~~
> {: .language-python}
>
> The index variable, loop variable, and dummy variable (they all mean the same thing) can be chosen freely, but it's a good idea to use a name that relates to the data you are processing.
{: .callout}


## Accumulators

One of the handy things about loops is that they can summarize a lot of data for us.  When using a spreadsheet, we frequently use `SUM` or `MEDIAN` or `MAX` to derive summary statistics.  Depending on our data structures, these may be applied directly, or we may prefer to use a loop to query for a summary directly.

**Direct Accumulators**.  If you are working with a data set that is all numeric, the following may help you identify certain values:

    values = [0.262998,0.189568,0.399016,0.544499,0.508346,0.444369,0.084814,0.361029,0.532302,0.679022]

    len(values)

    sum(values)

    min(values)

    max(values)

<!-- TODO exercise: `sorted` -->


To calculate values like the `median`, a library is necessary.  Libraries provide additional options when writing code.  Any complex process should be written once and used over and over again, and statistical functions not built directly into Python are no exception.

To load a library, we use `import`:

    import statistics

Once that is done, we use `library.` before the name of the function we intend to use:

    statistics.median(values)

    statistics.stdev(values)

    statistics.mode([1,3,4,5,1,2,3,4,1,5,2,3,3,4])

<!-- TODO exercise -->
<!-- TODO exercise: introduce math or numpy -->

**Loop Accumulators**.  Other quantities may require custom code to identify the desired summary.  For instance, finding the _second_-highest value

<!-- TODO lists and accums-->

Here's another loop that repeatedly updates a variable:

~~~
length = 0
for char in 'PCAOB':
    length = length + 1
print('There are', length, 'characters')
~~~
{: .language-python}

It's worth tracing the execution of this little program step by step.
Since there are five characters in `'PCAOB'`,
the statement on line 3 will be executed five times.
The first time around,
`length` is zero (the value assigned to it on line 1)
and `char` is `'P'`.
The statement adds 1 to the old value of `length`,
producing 1,
and updates `length` to refer to that new value.
The next time around,
`char` is `'C'` and `length` is 1,
so `length` is updated to be 2.
After three more updates,
`length` is 5;
since there is nothing left in `'PCAOB'` for Python to process,
the loop finishes
and the `print` statement on line 4 tells us our final answer.

Note that a loop variable is just a variable that's being used to record the progress in a loop.
It still exists after the loop is over,
and we can re-use variables previously defined as loop variables as well:

~~~
letter = 'z'
for letter in 'abc':
    print(letter)
print('after the loop, letter is', letter)
~~~
{: .language-python}

Note also that finding the length of a string is such a common operation
that Python actually has a built-in function (we will dig into functions later) to do it called `len`:

~~~
print(len('PCAOB'))
~~~
{: .language-python}

`len` is much faster than any function we could write ourselves,
and much easier to read than a two-line loop;
it will also give us the length of many other things that we haven't met yet,
so we should always use it when we can.

#### A Bit More on the `range` Function

Python has a built-in function called `range` that creates a sequence of numbers. `range` can
accept 1, 2, or 3 parameters.
* If one parameter is given, `range` creates an array of that length,
starting at zero and incrementing by 1.
For example, `range(3)` produces the numbers `0, 1, 2`.
* If two parameters are given, `range` starts at
the first and ends just before the second, incrementing by one.
For example, `range(2, 5)` produces `2, 3, 4`.
* If `range` is given 3 parameters,
it starts at the first one, ends just before the second one, and increments by the third one.
For example `range(3, 10, 2)` produces `3, 5, 7, 9`.
Using `range`, write a loop that uses `range` to print the first 3 natural numbers:
~~~
for i in range(1, 4):
    print(i)
~~~
{: .language-python}

#### How To `enumerate` a Container

In an earlier example, you used `range` and an index variable to count both where you were in a container and access that particular element.  There is a putatively easier approach:  use `enumerate` to count both the current index and the corresponding element.

~~~
for i, x in enumerate(interable_sequence):
    # Do something with i and x
~~~
{: .language-python}

> ## Challenge 1.2
>
> Exponentiation is built into Python:
>
> ~~~
> print(5 ** 3)
> ~~~
> {: .language-python}
>
> ~~~
> 125
> ~~~
> {: .output}
>
> Write a loop that calculates the same result as `5 ** 3` using
> multiplication (and without exponentiation).
>
> > ## Solution
> > ~~~
> > result = 1
> > for i in range(0, 3):
> >    result = result * 5
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Challenge 1.3
>
> Knowing that two strings can be concatenated using the `+` operator,
> write a loop that takes a string
> and produces a new string called "newstring" with the characters in reverse order,
> so `'CPA'` becomes `'APC'`.
> ~~~
> oldstring = 'CPA'
> ~~~
> > ## Solution
> > ~~~
> > newstring = ''
> > oldstring = 'CPA'
> > for char in oldstring:
> >    newstring = char + newstring
> > print(newstring)
> > # (ability power carrier?)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Challenge 1.4
> You have a list if lists called `a`
> Print out the position and the list in `a` that contains more than 2 elements AND starts with 1
> Hint: use `len()` to get the length
> ~~~
> a = [[1,2,3],[1,2],[1,2],[0,2,3],[1,2,4]]
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > a = [[1,2,3],[1,2],[1,2],[0,2,3],[1,2,4]]
> > for pos, lt in enumerate(a):
> >     if(len(lt)>2):
> >         if (lt[0] == 1):
> >             print (pos, lt)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
