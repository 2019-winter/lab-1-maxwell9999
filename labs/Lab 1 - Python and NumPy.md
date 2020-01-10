---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**Maxwell Taylor**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
```

```python
a = np.array([[2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2], [2, 2, 2, 2]])
a
```

```python
a = np.full((6, 4), 2)
a
```

## Exercise 2

```python
b = np.full((6, 4), 1)
np.fill_diagonal(b, 3)
b
```

## Exercise 3


Yes, a * b works cause the dimensions are the same. The dot product doesn't work because the number of columns in a is not equal to the rows in b.

```python
a * b
```

```python
np.dot(a,b)
```

## Exercise 4


The first transposes a to dot along the 6 axis and result in 4 x 4. Second does the opposite.

```python
np.dot(a.transpose(), b)
```

```python
np.dot(a, b.transpose())
```

## Exercise 5

```python
def helloWorld():
    display("Hello World") #could also use print

helloWorld()
```

## Exercise 6

```python
def outputStats(i, array):
    print("Array " + str(i) + " stats:")
    print("Mean: " + str(np.mean(array)))
    print("Sum: " + str(np.sum(array)))
    print("Median: " + str(np.median(array)))
    print("Max: " + str(np.amax(array)))

def genRandArrays():
    for i in range(4):
        outputStats(i, np.random.randint(10, size=(i+1)))
    
genRandArrays()
```

## Exercise 7

```python
def testfunc(x):
    c = 0
    for i in range(x.shape[0]):
        for j in range(x.shape[1]):
            if x[i,j] == 1:
                c += 1
    
    return c, len(np.where(a==1)[0])
display(testfunc(a))
display(testfunc(b))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
```

```python
dfA = pd.DataFrame(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
dfB = pd.DataFrame(b)
#b.iloc[range(4),range(4)] = 3
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
dfA * dfB
```

```python
dfA.dot(dfB)
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def testfunc(x):
    c = 0
    for i in range(x.shape[0]):
        for j in range(x.shape[1]):
            if x.iloc[i,j] == 1:
                c += 1
    
    return c, len(np.where(a==1)[0])
display(testfunc(dfA))
display(testfunc(dfB))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df.head()
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
```

```python
titanic_df.loc["female"]
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace = True)
titanic_df
```

```python

```
