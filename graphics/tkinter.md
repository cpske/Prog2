---
title: Tkinter Basics
---


## Elements of a Graphical Interface Framework

- [Window](#window) that is shown on screen
  - has title, menu bar
  - set-able attributes such as size, background color or image
  - includes a Container for content
  - `tkinter.Tk` and `TopLevel` are windows.

- [Container](#containers) that holds other components
  - a Container is a kind of Component that holds other components.
  - use Containers to group and layout a subset of the components separately, to simplify building a UI
  - Tkinter containers: `Frame`, `SplitPane`, ...

- [Components](#components) for items you can show in a window
  - Label, Button, Input Field, Radio Button, Checkbox, Combobox, Text Area
  - Components have a uniform set of attributes: height, width, background color, foreground color, padding

- [Layouts](#layouts) to manage positioning and sizing of components
  - Tkinter calls them "Geometry Managers" and the functionality is exposed via the components (as you'll see).
  - Tkinter Layouts: Grid, Pack, Place

- [Events and Event Handlers](#event-handling)
  - the framework defines different kinds of **events**, such as mouse click
  - you (application programmer) write code that should be run when one of these events occur, called **event handlers** or "callbacks".
  - event sources: user action, operating system, or code

- Event Loop
  - code provided by the framework that listens for events and dispatches events to event handlers

---------------------------------------------------------
## Window

In Tkinter the top-level window is `tkinter.Tk` (a class).  There should only be one per application.
```python
import tkinter as tk

# create only one window.  It is usually named "root".
root = tk.Tk()
root.title("Components Practice")
```

### Dialogs - Special Purpose Windows

* Messagebox
* Open File Dialog
* Yes/No Dialog
* OK/Cancel Dialog

See: [Pythontutor/tkinter](https://www.pythontutor.net/tkinter/)

Message box:
```python
import tkinter.messagebox

# information message
messagebox.showinfo("Confirmation", "Your response successfully submitted")
# error messag
messagebox.showinfo("Error Title", "Your response could not be submitted")
```


---------------------------------------------------------
## Components

When you create a component, the first parameter is always its *parent* container or window. Then you can specify optional **keyword parameters**.

```python
x = Component(parent, text="   ", padx=x, pady=y, onclick=function, fg="color", ...)

# Examples

button1 = Button(root)
button2 = Button(root, text="Press Me')
button3 = Botton(root, text="Press Me", fg="Red', onclick=handle_click)
```


| Component      | Example                         |
|----------------|---------------------------------|
| Label          | `Label(root, text="First name")`  |
| Button         | `Button(root, text="Press me")`  |
| Entry          | `Entry(root, width=50)`          |
| Radiobutton    | `Radiobutton(root, text="Choice 1", variable=choice, value=1)` |
|                | `Radiobutton(root, text="Choice 2", variable=choice, value=2)` |
| Checkbutton    | `Checkbutton(root, text="Check me")` |
| Scale          | vertical or horizontal slider    |
| Text (text area) | `Text(root, width=30, height=3)`, formatted text |
| Canvas         | a drawing area                   |
| Menu           | top-level, pulldown, or popup menu |
| Menubutton     | a popup or pulldown menu |
| Checkbox       |
| Radiobutton    |
| Listbox        | choose one or more items from a list |
| Scale          | select value using a slider  |
| Spinner        | select numerical value from range or list |

Components with event handler for click or Enter (Entry component).

```python
Button(root, text="press me", command=self.button_handler)
Button(root, text="Quit", command=self.destroy)
Entry(self, text="prompt message",  line of text")
`

### All Common Components with examples

* [Widgets](https://tkdocs.com/tutorial/widgets.html) and [More Widgets](https://tkdocs.com/tutorial/morewidgets.html) on [Tkdocs](https://tkdocs.com/tutorial/) - pages include many language bindins and are *long*

* [Tkinter Components](https://www.pythontutorial.net/tkinter/tkinter-listbox/) on <https://Pythontutorial.net/tkinter>. One page for each component, with explanation.

* [List of Tkinter Widgets](https://coderslegacy.com/python/list-of-tkinter-widgets/) with short code examples.


### Common Attributes for All Components

| Attribute            |
|:---------------------|
| `background="white"` (or `bg`) |
| `foreground="blue"`  (or `fg`) |
| `font=("Arial", 24)` |
| `padx=5`             |
| `pady=4`             |

Widget Attributes <https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/std-attrs.html>

1. Set or change attributes on a Component as dict entries:
   ```python
   button["background"] = "grey"
   button["foreground"] = "blue"
   label["text"] = "Goodbye Nerd"
   ```

2. Or use the `config` or `configure` methods:
   ```python
   button.configure(background="grey", foreground="blue")
   label.config(text="Goodbye Nerd")
   ```

Specify options as a dict (convenient for reusing them):
```python
options = {'padx': 5, 'pady': 5, 'font': ('Arial',12)}

button = tk.Button(parent, text="Press Me", **options)
```

## Tkinter.ttk Themed Components

Themed components (widgets) have their appearance controlled by a "theme" 
that specifies styling of all widgets using that theme, for a more
consistent appearance.

ttk provides all common Tk "widgets" such as:

| Styled Widget |
|:--------------|
| `ttk.Button`  |
| `ttk.Label`   |

and adds additional components:

| New Components |
|:---------------|
| `ttk.Combobox` |
| `ttk.Progressbar` |
| `ttk.Separator` |
| `ttk.Sizegrip` |
| `ttk.Treeview` |

### Defining a ttk Style

A style has a name and a collection of attributes:

```python
style = ttk.Style()
style.configure("dark", bg="black", fg="white", font=("Arial",14))
label = ttk.Label(parent, text="Mysterious label", style="dark")
button = ttk.Button(parent, text="Press me", style="dark")
```

---------------------------------------------------------
## Containers

A **container** is a Component that contains other Components.
Layout the components in a container the same way you would lay them out
inside a top-level window.

Use a Container (Frame) to group and arrange related components.
For example, use a Frame for the buttons on a keypad on a calculator.

| Container    | Provides       |
|--------------|----------------|
| Frame        | Empty area     |
| LabelFrame   | Frame with "lightweight" titlebar |
| PanedWindow  | 2 Adjustable Split Panes |
| Notebook     | Tabbed area      |
| TopLevel     | Top-level window that is shown on desktop |


The most common container is `tkinter.ttk.Frame`.

```python
import tkinter as tk
from tkinter import ttk
 
root = tk.Tk()
root.title("Container Example")

top = ttk.Frame(root, name="top", borderwidth=5, padding=5, relief="ridge")
bottom = ttk.Frame(root, name="bottom", borderwidth=5, padding=5, relief="ridge")
# add components to top Frame

# add components to bottom Frame
```

---------------------------------------------------------
## Layouts

Called "Geometry Managers" manage the size and relative position of components. They also resize the components when the window is resized.

- `grid` a flexible 2D grid layout. Grid cells can have different sizes and a component can span multiple cells.
  ```python
  button.grid(row=1, column=2, sticky=tk.E)
  ```
- `pack` the most primitive layout, but OK for simple designs
  ```python
  label.pack()  # use next available space
  ```
- `place` uses absolute positioning and sizing of components.  This should be avoided since the results depend on display resolution and do not resize well.
  ```python
  label.place(x=100, y=150)
  ```

`grid` is the most flexible layout:

```python
component.grid(row=r, column=c, sticky=string)
```
`r` is the row number starting from 0 at top,    
`c` is the column number starting from 0 at left,
`sticky=` specifies which edges of the grid cell the component should "stick" to. Can be any combination of "N", "S", "E", "W".  `tk` has constants for these strings, which you should use.

```python
label.grid(row=1, column=0, sticky=tk.E)  # stick to "East" (right) edge
entry.grid(row=1, column=1, sticky=tk.EW) # stick to both edges (fill the cell)
button.grid(row=1, column=1)              # not sticky. Retains natural size.
```

---------------------------------------------------------
## Control Variables

Many Tk components use a *control variable* to get/set attributes of a component.  These variables can generate events, so your code can be notified when the value changes.

| Control Variable    | Type of Value  |
|---------------------|----------------|
| tk.StringVar()      | str            |
| tk.IntVar()         | int            |
| tk.DoubleVar()      | double         |
| tk.BooleanVar()     | bool           |

to add an event handler to a control variable use:
```python
var = tk.StringVar()   # or any control var
var.trace(...)
```
---------------------------------------------------------
## References

* [Tkinter 8.5 reference](https://tkdocs.com/shipman/) the best Tkinter introduction and reference, by John Shipman at New Mexico Tech.
  - [mirror](https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/index.html)
  - [PDF](https://tkdocs.com/shipman/tkinter.pdf)
* Widgets <https://tkdocs.com/tutorial/widgets.html> on <https://tkdocs.com/>.
* Widget Attributes <https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/std-attrs.html>
* [Python 3.9 Tkinter Docs](https://docs.python.org/3.9/library/tkinter.html)
* <https://python-course.eu/tkinter/> on [Python-course.eu](https://python-course.eu) another good intro & reference.

