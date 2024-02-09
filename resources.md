---
title: Resources
---

### Online Books & Tutorials

- [Composing Programs](http://composingprograms.com/) from MIT. Chapter 1 is Functional Programming, which we will cover.
- [LearnPython](https://www.learnpython.org/) collection of topic-specific tutorials. The book *Learn Python* is one of the best Python books, but *too long*.
- [Real Python](https://realpython.com) is a collection of tutorials, including advanced topics.  Some parts are paid access, others are free.
- [Invent With Python](https://inventwithpython.com) has several books. Online versions are free.
- [Think Python](https://greenteapress.com/thinkpython2/html/thinkpython2018.html) or [PDF](https://greenteapress.com/thinkpython2/thinkpython2.pdf) textbook from Programming 1.
- [Python Books on Github](https://github.com/pamoroso/free-python-books)

### Python Visual Tutor

[www.pythontutor.com](www.pythontotor.com)
visualizes what Python code is doing to memory.

### Free Online Courses

These are highly recommended by multiple sources, but I have not tried them myself.

- [Intro to Python](https://www.datacamp.com/courses/intro-to-python-for-data-science/) at [DataCamp](https://www.datacamp.com).
- [Python for Everyone](https://www.py4e.com/lessons) basic and intermediate Python
- Jupyter Notebooks for [Interactive Data Science](https://github.com/mlund/jupyter-course), material on Github.
- [Introduction to Interactive Programming in Python, Part 1](https://www.coursera.org/learn/interactive-python-1) and [Part 2](https://www.coursera.org/learn/interactive-python-2) on Coursera, for beginners. Teaches interactive and graphical programming.


## Anaconda and Miniconda Python Distributions

In the 2nd half of the course you will use numpy, scipy, pandas, and Jupyter notebooks. You can add these packages to your current Python 3 installation, or install everything at once (including Python) using the "Anaconda" or "Miniconda" bundles.

* [Anaconda](https://www.anaconda.com/download) approx 660 MB
* [Miniconda](https://conda.io/miniconda.html) approx 60 MB (much smaller, but you can add to it)


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
