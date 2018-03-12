---
title: Python basics 2 - Conditional statements and Loops
teaching: 30
exercises: 0
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
Conditional statements are if-then statements: 
```
if BOOLEAN:
    DO SOMETHING 
``` 
This means, when the boolean is true, the INDENTED line "DO SOMETHING" will run. If the boolean is false, nothing will happen.  
You can add a second level of conditional statement like this:  
```
if BOOLEAN1:
    DO THING1 
    if BOOLEAN2:  
        DO THING2 
``` 
We determine the level with [indentation](https://docs.python.org/2.0/ref/indentation.html). For example, in the statement above, line 1 will run no matter what. Line 2 and 3 are at the same level, they will run only if line1's condition is met. Line 4 will run only if line 3's condition is met. <br>
- Note that if you are a MAS student, you have probablly learned other programming languages in CS 105 that uses {} braces for conditional statements. In Python, indentations works like the {} in javascript, or java, or c++, etc. <br>
- Indentation kind of forces you to make conditional statements look nice and clear. But if you printed your code on paper, and the conditional statement takes few pages, you might need a ruler to read it... Anyway, let's try this: <br>

```
a = 1
b = 3
if (a == 1):
    print("a is one!")
    if (b = 2): 
        print ("b is two!")
```
One important thing to notice in the code above is that we use a double equals sign `==` to test for equality rather than a single equals sign because the latter is used to mean assignment.
We can also combine tests using `and` and `or`. `and` is only true if both parts are true:

~~~
if (1 > 0) and (-1 > 0):
    print('both parts are true')
else:
    print('at least one part is false')
~~~
{: .language-python}

You can also add `elif` (else if) to add another situations, or add `else` to cover the rest of the situations.
```
if BOOLEAN:
    DO THING1
elif BOOLEAN: 
    DO THING2
else: 
    DO SOMETHING ELSE
```
> ## Challenge 1.1
>
> Consider this code:
>
> ~~~
> if 4 > 5:
>     print('A')
> elif 4 == 5:
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
One of the greatest things about programming is that machines can do repititive things for you. We will soon be dealing with 90,000 rows of data, loops will be very helpful for you. 
An example task that we might want to repeat is getting every elements in a list. 
~~~
assertions = ["Existance","Rights and Obligations","Completeness","Valuation and Allocation"]
~~~
{: .language-python}

(Look familiar, accountants?) <br>
We can access a element in a list using its index. For example, we can get the first
element of the list by using `assertions[0]`. One way to print each character is to use
four `print` statements:

~~~
print(assertions[0])
print(assertions[1])
print(assertions[2])
print(assertions[3])
~~~
{: .language-python}

This is a bad approach because it doesn't scale: if we want to print the list that has hundreds of elements, we'd be better off just typing them out.  

Here's a better approach:

~~~
assertions = ["Existance","Rights and Obligations","Completeness","Valuation and Allocation"]
for assertion in assertions:
    print(assertion)
~~~
{: .language-python}

This is shorter --- certainly shorter than something that prints every element in a hundred-element list --- and
more robust as well.

The improved version uses a [for loop]({{ page.root }}/reference/#for-loop)
to repeat an operation --- in this case, printing --- once for each thing in a sequence.
The general form of a loop is:

~~~
for variable in collection:
    do things with variable
~~~

We can call the [loop variable]({{ page.root }}/reference/#loop-variable) anything we like,
but there must be a colon at the end of the line starting the loop,
and we must indent anything we want to run inside the loop. Unlike many other languages, there is no
command to signify the end of the loop body (e.g. `end for`); what is indented after the `for` statement belongs to the loop.

> ## What's in a name?
>
>
> In the example above, the loop variable was given the name `assertion`.  
> We can choose any name we want for variables. We might just as easily have chosen the name `nyan_cat` for the loop variable, as long as we use the same name when we invoke the variable inside the loop:
>
> ~~~
> assertions = ["Existance","Rights and Obligations","Completeness","Valuation and Allocation"]
> for nyan_cat in assertions:
>     print(nyan_cat)
> ~~~
> {: .language-python}
>
> But don't name all your variables nyan_cat, it is a good idea to choose variable names that are meaningful, otherwise it would be more difficult to understand what the loop is doing.
{: .callout}

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

Note that a loop variable is just a variable that's being used to record progress in a loop.
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

#### Range function

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
For exmaple `range(3, 10, 2)` produces `3, 5, 7, 9`.
Using `range`, write a loop that uses `range` to print the first 3 natural numbers:
~~~
for i in range(1, 4):
    print(i)
~~~
{: .language-python}

#### Enumerate  
This is also a useful way to traverse an iterable sequence (for example, go throught everything in a list). 
The built-in function `enumerate` takes a sequence (e.g. a list) and generates a
new sequence of the same length. Each element of the new sequence is a pair composed of the index
(0, 1, 2,...) and the value from the original sequence:
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
> Print out the position and elements of the list in `a` that contains more than 2 elements AND starts with 1
> Hint: use `len()` to get the lenth  
> ~~~
> a = [[1,2,3],[1,2],[1,2],[1,2],[0,2,4]]
> ~~~
> {: .language-python}
>
> > ## Solution
> > ~~~
> > a = [[1,2,3],[1,2],[1,2],[1,2],[1,2,4]]
> > for pos, lt in enumerate(a):
> >     if(len(lt)>2):
> >         print (pos, lt)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}
