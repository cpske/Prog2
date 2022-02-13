---
title: Graphic and Graphical User Interfaces
---

- [Graphics Frameworks for Python](#graphics-frameworks-for-python)
- Presentation: [Intro to Graphics and Tkinter](graphics-intro.pdf) and my [Tkinter summary](tkinter) 
- [Learn Tkinter](#learn-tkinter) tutorials
- [Tkinter References](#tkinter-references) for details

2021 Lectures by Aj. Chaiporn

- [Lecture 4: Intro to GUI and Event-Driven Programming](https://drive.google.com/file/d/1PBhFr_VP2o_RVflNswjKMYKKWqUwuBEi/view) (PDF),
  video [part 1](https://drive.google.com/file/d/1BS6b7yPFyGw0_Ck20AG138TIYb5u1mhC/view) [part 2](https://drive.google.com/file/d/1RmJ77xUHExMdKAnpMA49vKGf1AJ874nm/view)
- [Lecture 5: Containers, Geometry Managers, and Canvas](https://drive.google.com/file/d/1rT6uxvFJdTvT33FNWLgW9JwGp9Idyy21/view),
  [Example Code](https://docs.google.com/document/d/1dHkmmMn1RtHe4-LZJjCQo3OmJwMYI4X2EdcFTg_7m10/),
  video [part 1](https://drive.google.com/file/d/1cT7V3v5t3oUmntG5BEN2NaOak2Aq4GZi/view), [part 2](https://drive.google.com/file/d/1Yo0zxMEOB3T7QIC9V1HadKKk3g8cW8xL/view)    
- [Lecture 6: Long-Running Tasks and Animation](https://drive.google.com/file/d/1sjtnCrT0O5Hya3kZ45axSa8oylXJ_6_S/view),
  [Example Code](https://docs.google.com/document/d/1LJ5YwK96rnlFvQRRQhv-jATgYLdAVkjTIMITeiqToFc/),
  video [part 1](https://drive.google.com/file/d/1icC_v8kMiS_mAlhC6D__fGv15sgrcFVF/view), [part 2](https://drive.google.com/file/d/1eg1Ei_HQaop8U2Jf1EDU5Uk-_PnOv60t/view)



## Graphics Frameworks for Python

The "best" GUI frameworks for Python are:

1. [Tkinter][Tkinter] - part of the Python distribution and has lots of learning resources and add-on packages.  API is kind of clumsy (strings for setting non-string attributes) and inconsistent. Lacks a clear separation between layout managers and containers.  Official documentation sometimes refers to Tk/Tcl documentation, which is not helpful (who has time to go read the Tk/Tcl documentation and then *translate* the function calls to their Python equivalent).

2. [PyQt5][PyQt5] built on the Qt cross-platform GUI framework.  Powerful and extensive framework, but requires Qt5 (heavy-weight framework) be installed, too. PyQt4 and PyQt5 are developed by a private company and has some licensing requirements.

3. [wxPython][wxPython] a wrapper for the wsWidgets API, to create platform-native user interfaces.

4. [Kivy][Kivy] open-source and based on OpenGL, suitable for creating GUI and graphical games.

5. [libavg][libavg] light-weight framework for creating UI for touch-based devices.

Ref: [6 Best Python GUI Frameworks](https://pythongui.org/6-best-python-gui-frameworks-in-2021/), December 2021.

[Tkinter]: https://wiki.python.org/moin/TkInter
[PyQt5]: https://www.riverbankcomputing.com/software/pyqt/
[wxPython]: https://wxpython.org/
[Kivy]: https://kivy.org/
[libavg]: https://www.libavg.de/site/


## Learn Tkinter

- [Introduction to Tkinter](https://www.cs.mcgill.ca/~hv/classes/MS/TkinterPres/) on cs.mcgill.ca.  Comprhensive, readable description as a single web page.
- [Tkinter Tutorial](https://www.pythontutorial.net/tkinter) on <https://www.pythontutorial.net>.
- [Tkinter reference](https://tkdocs.com/shipman/) by John Shipman includes a lot of example code.
- <https://python-course.eu/tkinter/> on [Python-course.eu](https://python-course.eu) another good intro & reference.
- Widgets <https://tkdocs.com/tutorial/widgets.html> on <https://tkdocs.com/>.
- [Thinking Tkinter](http://thinkingtkinter.sourceforge.net/) explains concepts behind Tkinter apps using a sequence of simple Python apps. Includes a lot of "how to" for event binding and event handlers.
- *Tkinter Programming* by Jan Bodnar, PDF document (free online).


## Tkinter References

The most readable Tkinter reference is by John Shipman at New Mexico Tech.

- [Tkinter 8.5 reference](https://tkdocs.com/shipman/) by John Shipman.
  - [mirror](https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/index.html)
  - [PDF](https://tkdocs.com/shipman/tkinter.pdf)
- [Python 3.9 Tkinter Docs](https://docs.python.org/3.9/library/tkinter.html)
- Widget Attributes <https://anzeljg.github.io/rin2/book2/2405/docs/tkinter/std-attrs.html>
- [Python 3.9 Tkinter Docs](https://docs.python.org/3.9/library/tkinter.html)
- <https://python-course.eu/tkinter/> on [Python-course.eu](https://python-course.eu) another good intro & reference.
- <https://tkdocs.com/> is a detailed reference with excellent explanation of Tk concepts. It covers multiple language bindings (Bash, Ruby, Perl, Python, and Tcl) which makes the pages very long and harder to navigate. Also has a tutorial.

