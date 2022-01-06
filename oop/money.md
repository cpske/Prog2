---
title: OO Programming Example and Python Review
---

## Starter Code

Please clone this assignment from Github Classroom -- URL given in class.

## Money

Money is a unit of exchange having a value and a currency.

Money is *fungible*, meaning that any two objects having same value and currency are equivalent.

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

## Exercise: Add a String Method

```python
>>> m1 = Money(10, "Baht")
>>> print(m1)
<Money object at 0x7fcf9ac13978>

>>> str(m1)
'<Money object at 0x7fcf9ac13978>'
```
(the number is the object's address in memory)

* Where did this ugly string come from?

**Exercise**: write a `__str__` method to print the money nicely, such as:
```
10 Baht
1,000 Baht
0.50 Baht
```
try to write simple, clean code without a lot of "if - else".

Hint: `x = 1234.5678`, `print(f"{x:,.2f}")`


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
```

In most applications, an object's attributes should be protected from direct
modification by other parts of the code.  This ensures data integrity and
gives the programmer freedom to change the way a class is implemented.

We want to protect the value from change outside of the class.

You can make the "value" be read-only (*immutable*) in two steps:
1. change the attribute name to `_value`
2. write a `@property` named "value" that returns the `_value`

```python

    def __init__(self, value, currency):
        self._value = value
        self.currency = currency

    @property
    def value(self):
        return self._value
```

**Try it!**
```shell
>>> m = Money(10, "Baht")
>>> m.value
10

>>> m.value = 1000
AttributeError: can't set attribute
```

## Throw Exceptions When Something is Wrong

You studied exceptions in Programming 1.

What are the 2 most common exception types in Python?

If you don't know, try this:
```python
s = "hello"
s + 3
```
and:
```python
import math
math.sqrt(-1)

import datetime
# create a date: date(YYYY, M, D)
day = datetime.date(2022, 1, 32)
```

|   Exception        | Meaning             |
|--------------------|---------------------|
|                    | Value of an argument is not allowed. |
|                    | Type of an argument is incorrect or incompatible. |

### How to Raise an Exception

The Exception classes allow you to specify a string message:
```python
def foo(x):
    """x must be an int."""
    if not isinstance(x, int):
        raise TypeError("Argument must be type 'int'")
```
when you raise an exception, the program flow exits the method or function immediately.

## Money Should Raise Exceptions

- if the currency is not a `str` raise a TypeError
- if the currency is an empty string, raise a ValueError
- if the value is not an int or float, raise a TypeError

## Avoid String Literals for Special Values

In Money, the currency is a string.  This can result in inconsistencies:
```python
m1 = Money(10, "Baht")
m2 = Money(10, "baht")
m3 = Money(10, "THB")
```

You should avoid using string constants in code for things that have special meanings. 

There are 2 solutions for this.

1. If you need only one currency, define a string constant. In Python, names of constants should be in UPPERCASE.
   ```python
   CURRENCY = "Baht"
   m1 = Money(10, CURRENCY)
   ```
2. If you need to use several currencies, define an Enum.  An Enum is like a class with a fixed set of static attributes.  We'll study Enum later.
It would be better to have a fixed set of currencies instead of using strings.



## Summary

1. Implement "magic methods" to provide needed behavior.
2. Class "members" with names beginning in underscore (`_`) should be treated as private. Don't directly access them, except inside the class or a subclass.
3. Protect attributes from change (when desired) using properties.
4. Document classes and public methods by writing *docstring* comments, including the meaning of parameters and return values.  It is OK to omit details for simple, obvious methods like `__str__`.
5. Raise an exception when something is wrong. Don't silently ignore errors.
6. Use a named constant for special values, not string or numeric literals.
