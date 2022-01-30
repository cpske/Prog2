---
title: Feedback
---

## Feedback on Wallet


### Polymorphism: "*Don't Ask What Type*"

When using polymorphism, you should **not** need to check the actual
type of an object:

```python
    if isinstance(x, Coin):
        self.items.append(x)
    elif isinstance(x, Banknote):
        self.items.append(x)
```
also wrong:
```python
    if isinstance(x, (Banknote,Coin)):
        self.items.append(x)
```


**Try This:**   True or False?
```python
>>> c = Coin(5, "Baht")
>>> isinstance(c, Cash)
```

Coin and Banknote **behave the same** as Cash.  Therefore, the Wallet can treat them all as Cash.


#### The Wallet Class Should NOT Depend on Coin or Banknote

If it does, your code may not work when some other kind of Cash is added.


### Duplicate Code in str Method

```python
class Coin(Cash):

    def __str__(self):
        if int(self.value) != self.value:
            return f"{self.value:,.2f} {self.currency} Coin"
        return f"{int(self.value):,} {self.currency} Coin"

class Banknote(Cash):

    def __str__(self):
        if int(self.value) != self.value:
            return f"{self.value:,.2f} {self.currency} Banknote"
        return f"{int(self.value):,} {self.currency} Banknote"
```

Problem with this:

1. **Duplicate Logic** - "if value is integer then print ... else ..."
2. **Waste of Time** typing duplicate code

### Better str Method

```python
class Coin(Cash):

    def __str__(self):
        return super().__str__() + " Coin"

class Banknote(Cash):

    def __str__(self):
        return super().__str__() + " Banknote"
```

### Even Better: Refactor to superclass

**How to Get the String Name of an Object's Class?**

Try this:
```python
>>> c = Coin(5, "Bananas")
>>> type(c)
cash.Coin
>>> type(c).__name__

what does it print?
```

```python
class Cash(Money):

    def __str__(self):
        """a string representation that includes actual class name"""
        classname = type(self).__name__
        return super().__str__() + " " + classname
```

### Duplicate Code in repr() Method

```python
class Coin(Cash):
    def __repr__(self):
        return f"Coin({self.value},'{self.currency}')"

class Banknote(Cash):
    def __repr__(self):
        return f"Banknote({self.value},'{self.currency}')"
```

**Are you bored yet?**


### Learn a Programming Language Well and Use it Fluently

Learn your programming language **very well**.  Avoid these problems:

* waste time writing extra code for things the language provides
* errors due to misunderstanding of what the code does

> Employers say they want programmers to know one or two languages very well,
> rather than know a little about many programming languages.
>
> It's useful to know several programming languages, but you should strive to master at least one.


In `Wallet`:

```python
def deposit(self, *args):
   # after checking that args are all valid

   # this is clumsy & inefficient
   for i in range(len(args)):
        self.items.append(args[i])
```

better but still not necessary:
```python
   for item in args:
        self.items.append(item)
```

append a collection to existing list:
```python
   self.items.extend(args)
```
### Do Not Put Top-Level Executable Code in a Module that Other Code will Import

Every time you `import something`, any top-level code in `something.py` is executed.

In wallet.py
```python
class Wallet:
    ...


# some test code
wallet = Wallet()
wallet.deposit(Coin(5,"Baht"), Banknote(20,"Baht"))
print("Balance is", wallet.balance())
```

The test code is executed every time wallet is imported (as in unit tests).

### Remove TODO Comments When Done!

"TODO" comments are a common programming convention.
The IDE recognize them and will show them in a special panel.

PyCharm even has a "TODO" tab at the bottom (example: wallet-start).

Please **remove the TODO comments after you do them**.
Don't submit code with "TODO", unless you didn't do it.

```python
class Cash(Money):

    def __init__(self, value: float, currency):
        """Initial a new cash object. value must be positive."""
        #TODO verify the value is positive
```

or
```java
public void add(Money other) {
    //TODO add assert statements that other is not null or wrong currency

```
