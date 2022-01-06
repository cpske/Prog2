## Iterables and Iterable

The Python `collections` module has ABC classes named `Iterable`
and `Iterator`.

* **Iterator**: something is an Iterator if you can retrieve the elements one-by-one by calling `next(obj)`. The `next()` function calls the object's own `__next__()` method. 
Unlike Java (and the Iterator Design Pattern), Python iterators do not have a "hasNext()" method.
 The motivation for Iterators comes from the *Iterator Design Pattern*.  
* **Iterable**: an object is Iterable if it has a `__iter__()` method that returns an Iterator.  The programmer should not call this method himself; instead use `iter(object)` to get an iterator.

Strings, Ranges, and sequences are iterable.

Here's an example:
```python
import collections
s = "hello
instancesof(s, collections.Iterable)
```
prints `True`.  So lets get an iterator and iterate:
```python
it = iter(s)
while True:
   print( next(it) )
```
prints:
```
h
e
l
l
o
Traceback (most recent call last):
StopIteration
```

The `for x in obj` statement works for any *Iterable* `obj`.  It creates an iterator from `obj` nad uses it to get the elements.

`

