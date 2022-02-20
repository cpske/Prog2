---
title: Feedback on Lab 6 Converter
---

Things to **test**:

- Press "Convert" when both input fields are empty. Many codes print exception on the console.

- Enter a non-integer value to convert. A few codes only allow "int".

- Enter a value in right-side input field and press "Convert". Does it convert right-to-left?

- Can you resize the window?  Should be resizable.

- (Good code) If you expand the window, do the input fields expand?  That's good.

**Code Review**: Problems to look for in `converter_ui.py`.

- Must **not** create components in `__init__`.  But OK to create control variables. Create components in `init_components`.
- Should **not** set `self.geometry(NNNxMMM)`.  Let Geometry Manager determine window size.
- Should **not** set `self.resizable(False)`.  This is almost always bad.
- Using Labels to add space between fields?  Should set padding instead.
- Creating Combobox in `load_units`. `load_units` should put units in existing comboboxes.


Problems seen in student code:

## 1. Using labels to add space between components.

This is cludgy. A programmer should develop an internal sense of
what is a poor solution, and avoid doing those things. (*PAD: Quick Fixes Become Quicksand*)

```python
label = tk.Label(text=" ")
label.grid(row=0, column=0)
label = tk.Label(text=" ")
label.grid(row=0, column=6)
label = tk.Label(text="=")
label.grid(row=0, column=7)
label = tk.Label(text=" ")
label.grid(row=0, column=11)
label = tk.Label(text=" ")
label.grid(row=0, column=13)
entry1 = tk.Entry(self, width=18, textvariable=self.entry_1)
entry1.grid(row=0, column=4)
entry2 = tk.Entry(self, width=18, textvariable=self.entry_2)
entry2.grid(row=0, column=9)
convertbutton = ttk.Button(self, text='Convert', command=self.convert_handler)
convertbutton.grid(row=0, column=12)
```

This code is hard to read and easy to make mistakes with the column numbers.
No one would want to modify something like this.

To add padding around a component use the optional parameters `padx` and `pady`.
You can also using `ipadx` and `ipady` to add padding *inside* a component.
Examples: <https://www.pythontutorial.net/tkinter/tkinter-grid/>

Two Ways (one terrible, one OK):

* explicitly add to each component:
  ```python
  entry1.grid(row=0, column=1, padx=5, pady=5)
  combobox1.grid(row=0, column=2, padx=5, pady=5)
  eq_label.grid(row=0, column=3, padx=5, pady=5)
  etc.
  ```
* use a dict of extra parameters for components
  ```python
  options = {'padx': 5, 'pady': 5}
  entry1.grid(row=0, column=1, **options)
  combobox1.grid(row=0, column=2, **options)
  eq_label.grid(row=0, column=3, **options)
  etc.
  ```
* See below for how to make the code less redundant.


## 2. Create New Comboboxes in `load_units`

The purpose of `load_units` is to set the unit names in the comboboxes.
You **should not** create new Combobox objects in `load_units`.

Someone wrote this:
```python
    def load_units(self, unittype: UnitType):
        """Load units of the requested unittype into the comboboxes."""
        units = self.converter.get_units(unittype)
        # Combobox 1
        combo1 = ttk.Combobox(self, textvariable=self.combo1)
        combo1.grid(row=0, column=5)
        combo1['values'] = list(units)
        combo1['state'] = 'readonly'
        # Combobox 2
        combo2 = ttk.Combobox(self, textvariable=self.combo2)
        combo2.grid(row=0, column=10)
        combo2['values'] = list(units)
        combo2['state'] = 'readonly'
```
Do not create new comboboxes. Just set the values in the existing boxes.

It should be clear that this is **bad code**.


## 3. No value displayed in combox boxes on startup

In `load_units` it should select a unit value (if there is one) instead of showing an empty combobox.

In my code, I select the 1st unit in left combobox and 2nd unit in the right combobox, since converting a unit to itself is useless.


## 4. Bad Logic in `convert_handler`

Many students seem to (almost deliberately) use bad logic.

Instead of checking "is there a value in box1?" this code checks "is box2 empty?"
They are not the same.  As a result, this code will raise exception if both boxes are empty when "Convert" is pressed:

```python
if self.entry_2.get() == "":
    conv = self.converter.convert(
                float(self.entry1.get()), self.combo1.get(), self.combo2.get())
    self.entry2.set(conv)
else:
    conv_2 = self.converter.convert(
                  float(self.entry2.get()), self.combo2.get(), self.combo1.get())
    self.entry1.set(conv_2)
```

## 5. Don't Use Fixed Size Window!

Isaraa wrote this:

```python
    def __init__(self, converter: UnitConverter):
        super().__init__()
        # save a reference to the unit converter
        self.converter = converter
        self.geometry("790x40")
        self.resizable(False, False)
```

**Do not** set the window size and **almost never** set `resizable(false)`.

I mentioned this is class. The UI should manage it's own size.
What if the user wants a wider window in order to see more digits of the conversion?

These students wrote `self.resizable(False, False)` (even though you only need to write **one** parameter):

```python
| Student | Bad Code |
|---------|----------|
| Isaraa |   self.resizable(False, False) |
| Jitpanu |  self.resizable(False, False) |
| Khongnat | self.resizable(False, False) |
| Kittiporn | self.resizable(False, False) |
| Kodchakan | self.resizable(0,0) |
| Maroj |     self.resizable(False, False) |
| Napasakorn | self.resizable(False, False) |
| Noppharut |  self.resizable(False, False) |
| Panupun |    self.resizable(False, False) |
| Pawitchaya | self.resizable(False, False) |
| Pawitchaya | prompt_win.resizable(False, False) |
| Piyawat |    root.resizable(False, False) |
| Punn |       self.resizable(False, False) |
| Setthanan |  self.resizable(False, False) |
| Siravich |   self.resizable(False, False) |
| Supakrit |   self.resizable(False, False) |
```

These students also set the window size instead of letting it size to fit the components:

| Student | Bad Code |
|---------|----------|
Danita     | self.geometry('1020x39') |
Isaraa     | self.geometry("790x40") |
Kulisara   | self.geometry('1000x50') |
Maroj      | self.geometry("750x30") |
Noppharut  | self.geometry("500x50") |
Panupun    | self.geometry("750x25") |
Pawitchaya | self.geometry("615x135") |
Pawitchaya | prompt\_win.geometry("300x100") |
Piyawat    | root.geometry('300x70') |
Preawpan   | self.geometry('1000x50') |
Setthanan  | self.geometry('780x50') |
Siravich   | self.geometry("720x40") |
Thanadol   | self.geometry('730x40') |
Thanida    | self.geometry('800x40') |
Wongsathorn | self.geometry("800x40") |





## Less Boring Code: Automatic Column Calculation

Are you **sick** of manually entering the column values yet?

```python
options = {'padx': 5, 'pady': 5}
entry1.grid(row=0, column=0, **options)
combobox1.grid(row=0, column=1, **options)
eq_label.grid(row=0, column=2, **options)
entry2.grid(row=0, column=3, **options)
combobox2.grid(row=0, column=4, **options)
convertbutton.grid(row=0, column=5, **options)
```

What does this print?  
```python
# an iterator for integers
n = iter(range(50))    # or use itertools.count()
next(n)
next(n)
next(n)
```

So how about this?
```python
options = {'row': 0, 'padx': 5, 'pady': 5}
column = itertools.count()
entry1.grid(column=next(column), **options)
combobox1.grid(column=next(column), **options)
eq_label.grid(column=next(column), **options)
entry2.grid(column=next(column), **options)
combobox2.grid(column=next(column), **options)
convertbutton.grid(column=next(column), **options)
```

Not DRY enough?  How about this:
```python
options = {'padx': 5, 'pady': 5}

# components in the order they should appear
components = [entry1, combobox1, eq_label, entry2, combobox2, convertbutton]

# apply grid layout to all components
column = itertools.count()
for component in components:
    component.grid(row=0, column=next(column), **options)
```

