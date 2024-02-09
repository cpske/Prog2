## Iterator and Iterable (Extra Material)

In the next few weeks we'll study *iterators*, which are a common feature of many languages.
For the curious, here's a preview.

### Make CourseList be *Iterable*

We would like to be able get all a student's enrollments using a `for` loop like this:

```
for enrollment in courselist:
    print(enrollment.course.course_id, enrollment.grade)
```

To do this, we add an "iterator" method to `CourseList` that simply returns an *iterator* over the list of Enrollments:

```python
    def __iter__(self) -> Iterator[Enrollment]:
        """Return an iterator for the enrollments in this courselist."""
        return iter(self.enrollments)
```

Then any code can *iterate* over the enrollments like this:
```python
courselist = CourseList(student)
courselist.add_course(Course("01219116", "Programming 2", 3))
courselist.add_course(...)

# get an iterator
iterator = iter(courselist)
print(next(iterator))
# prints first course
print(next(iterator))
# prints second course
```

This is so useful that it is considered a *Design Pattern* called the *Iterator Pattern*.

 *Iterable* as shown below.  Add this to the class diagram.
   - The `__iter__` method returns an *Iterator* over the Enrollments.
   - In UML, show `Iterable` as an interface with an `__iter__` method
   - Show CourseList *implements* Iterable
   - Types like Iterable show that a class *has* a particular method(s), without the type providing an implementation of the method(s). This is exactly what *interfaces* do.
 

```python
from typing import Iterable, Iterator

class CourseList(Iterable[Enrollment]):

    def __iter__(self) -> Iterator[Enrollment]:
        """Return an iterator for the enrollments in this courselist."""
        return iter(self.enrollments)
```


## Iterable & Iterator

In Python, [Iterable][Iterable-refs] and [Iterator][Iterator-refs] are **types** (in the `typing` package) with
implementations as *abstract base classes* in the `collections.abc` package.

In Java, C#, and other languages, *Iterable* and *Iterator* are *interfaces*.
Since an **interface** is a specification for some behavior without an implementation,
Python *types* are conceptually like *interfaces*.

[Iterable-refs]: https://docs.python.org/3/search.html?q=Iterable
[Iterator-refs]: https://docs.python.org/3/search.html?q=Iterator
[iterable]: https://docs.python.org/3/library/typing.html?highlight=iterable#typing.Iterable
[iterator]: https://docs.python.org/3/library/typing.html?highlight=iterator#typing.Iterator

[Iterable][iterable] is used extensively in Python, even though you may rarely
call it explicitly.   

What kind of object can you use in each of these statements?
```python
for x in ___?what?___:
    do something with x
```
or 
```python
[foo(x) for x in ___?what?____ if predicate(x)]
```
or
```python
sorted_values = sorted(?what?)
```
In all three cases, you can use anything that is *Iterable*.


[Iterable][iterable] A class is *Iterable* if it's instances create an Iterator (for some sequence) when you invoke `iter(object)`.
- `CourseList(Iterable)` means CourseList implements Iterable.
- `Iterable[X]` means the iterators created by this Iterable returns objects of type X.
- `CourseList(Iterable[Enrollment])` means CourseList is Iterable and the Iterator returns Enrollment objects.
- list, set, dict, and strings are all Iterable.

[Iterator][iterator] is a type that *iterates* over a sequence of values each time `next()` is called.  Iterator specifies a single method `__next__` that is invoked by calling `next(iterator)`.

```python
s = "Strings are Iterable"
# get an iterator for this string
it = iter(s)
# iterate over the elements 
next(it)
'S'
next(it)
't'
next(it)
'r'
next(it)
'i'
```
You usually don't use an iterator explicitly. Iterator is used by `for` loops, list comprehensions, and other constructs.


### Python Syntax for Subclass, Implements, & Mixin

In Python, the same notation is used for inheritance, typing, and mixins:
```python
from collections.abc import Sized, Callable

class Subclass(Parent, Sized, Callable):
    """A class that is a subclass of Parent,
    and also has the Sized and Callable behavior.
    """
```

