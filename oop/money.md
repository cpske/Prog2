---
title: OO Programming Example and Python Review
---

## Starter Code

Please clone this assignment from Github Classroom -- URL given in class.

## Money

Money is a fungible unit of exchange having a value and a currency.


In Python, the starter code looks like:
```python

class Money:
    """Money represents a unit of value with a currency."""

    def __init__(self, value, currency):
        self.value = value
        self.currency = currency
```

We add behavior to satisfy some requirements, described below.

### When is Money Equal?

Money should be *fungible*.  That means all money with the same value
and same currency is equal.  Is it?

Try this:
```python
>>> m1 = Money(10, "Baht")
>>> m2 = Money(10, "Baht")
>>> m1 == m2
```

How to fix this?

### Magic Methods

Python classes have several "magic" methods whose names have the form `__methodname__`.

To see them, try this (output is easier to read if you use ipython interpretter):
```
>>> dir(str)
['__add__',
 ...
 '__eq__',
 '__doc__',
 '__gt__',
 '__repr__',
 '__str__',
 ...
]
```

They are called "magic" because Python invisibly calls them when you write certain expressions:

| What You Write  | What Python Invokes     |
|-----------------|-------------------------|
| `x == y`        | `x.__eq__(y)`           |
| `x > y`         | `x.__gt__(y)`           |
| `print(x)`, `str(x)` | `x.__str__()`      |
| `z = x + y`     | `z = x.__add__(y)`      |
| `z = x * y`     | `z = x.__mul__(y)`      |

## Write `__eq__` for Money

Write the code for `__eq__`:

1. Two Money objects are equal if they have the same value and currency.
2. Money is not equal to non-Money.  So `m1 == 10` should be False.

**Push your code to Github**.

### Lesson Learned

There is a standard "template" for an == method:

1. verify the argument belongs to the same class as `self`, or at least a compatible class.
2. compare the objects by value

### Writing Good Code

You should write Docstring comments in methods, esp. public methods.

```python
    def __eq__(self, other):
        """Two money objects are equal if they have same value and currency.

        Parameters:
            other - a Money object to compare to this
        Returns:
            True if they have same value and currency, otherwise False
```
There are other formats for writing docstrings.  
See [ ] for more details.

### Test Your Code

After writing `__eq__` verify that it works correctly in all cases.

| Test Case   | Expected Result |
|-------------|-----------------|
| same value, same currency | True  |
| same value, different currency | False |
| different value, same currency | False |
| different value and currency | False |
| compare to non-Money | False |

## Add 

## Characteristics of Object-Oriented Programming

The *Three Pillars* of OOP are:

1. Encapsulation -
2. Inheritance -
3. Polymorphism -

Describe each of these,
and explain how the simple Money class illustrates each of them.

## Better Encapsulation using Properties

Python does not have truly "private" attributes.
Other parts of a code can modify an objects attributes:
```python
m1 = Money(10.0, "Baht")
# print the value
print(m1.value)
# change the value to 10,000 Baht
m1.value = 10000



### OO Principles



