---
title: Resources
---

## Python Visual Tutor: [www.pythontutor.com](www.pythontotor.com)

Visualizes what Python code is doing to memory.

## Anaconda and Miniconda Python Distributions

In the 2nd half of the course you will use numpy, scipy, pandas and Jupyter notebooks. You can add these packages to an ordinary Python 3 installation, or install everything at once (including Python) using "Anaconda" or "Miniconda" bundles.

These distributions provide Python along with many packages and a virtual environment manager.

* [Anaconda](https://www.anaconda.com/download) approx 660 MB.
* [Miniconda](https://conda.io/miniconda.html) approx 60 MB.

## Online Books

- [Composing Programs](http://composingprograms.com/), especially Chapter 1 (Functional Programming)
- [LearnPython](https://www.learnpython.org/) collection of topic-specific tutorials. The book *Learn Python* is one of the best Python books, but *too long*.
- [Python Books on Github](https://github.com/pamoroso/free-python-books)
- [Invent With Python](https://inventwithpython.com) has several books. Online versions are free.
- [Think Python](https://greenteapress.com/thinkpython2/thinkpython2.pdf) beginning Python.

## Free Online Courses

These are highly recommended by multiple sources, but I have not tried them myself.

- [Intro to Python](https://www.datacamp.com/courses/intro-to-python-for-data-science/) at [DataCamp](https://www.datacamp.com).
- [Python for Everyone](https://www.py4e.com/lessons) basic and intermediate Python
- Jupyter Notebooks for [Interactive Data Science](https://github.com/mlund/jupyter-course), material on Github.
- [Introduction to Interactive Programming in Python](https://www.coursera.org/learn/interactive-python-1) on Coursera, 5 weeks for complete beginners. Teaches interactive and graphical programming.

## Paid Online Python Courses

[Top 3 Python Courses](https://medium.com/codingthesmartway-com-blog/top-3-python-online-courses-8091e0dc8a79) at *Coding the Smart Way*:

1. [Python Bootcamp: Go from zero to hero](https://codingthesmartway.com/courses/python-bootcamp/) 12.5 hours.  You can perform exercises online using Jupyter Notebooks. 330 Baht.
2. [Complete Python Master Class](https://codingthesmartway.com/courses/python-masterclass), 37.5 hours. 330 Baht.


## Intel's Python and Python Channel for Anaconda

Intel has a high-performance implementation of many Python libraries,
that are much faster than the standard Python libraries.
If you plan to do compute-intensive work in Python on an Intel CPU,
it is worth trying.  For just learning Python there is no benefit.

You can download [Intel Python](https://software.intel.com/en-us/distribution-for-python) as a separate distribution.
Or, add a "channel" to your existing Anaconda distribution.  
To add a channel to Anaconda:

```
conda update conda
conda config --add channels intel
# Now add various packages.  
# Some Conda packages will be replaced or downgraded with Intel verions.
conda install numpy scipy matplotlib sympy mkl
```
