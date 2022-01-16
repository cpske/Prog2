---
title: Introduction to the Course
---

This course covers 

1. Object-oriented design and programming, including some design patterns
2. Functional programming 
3. Writing good quality code
4. Graphical applications and graphical user interfaces using Tkinter
5. Data exploration and scientific programming using Jupyter Notebooks

### Course Objectives (What You Learn)

Learn to design, implement, and test applications with several components. Learn how to use libraries or frameworks to build on existing code, and to manage your code and project documents in a version control system; in particular, be able to use git and Github.

You should be able to use API documents to find information, and not rely on searching for solutions on StackOverflow.  You should also be able to write good documentation for your own code, using a standard format (Javadoc) and documentation generator.

You should learn guidelines for writing good quality code, 
including a coding convention and coding standard, 
and design principles and patterns to help you design good software.

### Effort 

You should commit several hours per week to read, program, and do assignments on their own. You need to do **reading** and **programming** to master the material. Don't rely only on videos.

Everyone must do the assigned work **individually**.  Please do not ask other students to "teach" you or copy anything from anyone else.
If you need help, please ask the TAs or instructors.

### Topics

The weekly topics are posted on Google Classroom. 
The course will cover at least [these topics](index).

Reading material will come from these [resources](resources) as well as the [online Python documentation](https://docs.python.org/3.9.0/).

### Course Work & Grading

The course and your grade include:

* class participation
* lab work
* programming assignments
* quizzes
* homework
* written exams 
* programming exams

**Minimum Exam Score:** To pass the course you must have an **average exam score at least 50%**.

If you achieve the minimum exam score, then the following grading scale is used based on your overall work:

| Overall | Grade |
|---------|-------|
|  > 85%  |   A   |
| 75-85%  |   B   |
| 65-75%  |   C   |
| 55-65%  |   D   |
|  < 55%  |   F   |

### Requirement for Individual Work

All assignments must be done **individually**, unless group work is explicitly allowed.

It is OK to discuss an approach to solving a problem, but not to share solutions or code.  If you need help, please ask the TAs or instructors rather than the other students (who may not give you the correct answer).

### if copy(): fail()

Anyone who submits **any** copied work will receive grade "F" and be reported to Faculty of Engineering for disciplinary action.

Both the copier and the person who knowingly supplied the material will receive "F" and be reported.

### Assignments using Github Classroom 

We use Github Classroom for assignments and quizzes. The way it works is:

1. For each assignment you are given the URL of the "invitation" to do the assignment.  
2. Visit the URL and "accept" the invitation.
   - First time: you may be asked to associate your real name with your Github account
3. Github Classroom then creates a repository for you. The repository may contain starter code and instructions.
4. Wait a few seconds and refresh the page to see the URL of your repo.  **Click** on the URL to go to your repo.
5. Clone the repository to your computer and do the work.
6. Add your work, "commit", and "push" to Github.
   - You can commit and push many times during a quiz or assignment.  
   - It is a good idea to commit & push your work regularly to avoid losing work.

**Example**

Your Github ID is `spiderman` and the assignment url is http://bit.ly/lab1.

* Visit http://bit.ly/lab1 and accept the assignment.
* Refresh the page. Github shows it created a repo for you at url:
  ```
  https://classroom.github.com/prog2022/lab1-spiderman
  ```
* Click on the link to visit your repo, so you can see the files and formated README.
* Clone the repository to your computer. Using the command line:
  ```shell
  # change to a directory where you store programming work
  cmd> cd /somepath/prog2/workspace
  cmd> git clone https://classroom.github.com/prog2022/lab1-spiderman
  ```
  This will create a local directory named `lab1-spiderman` containing your work.    
  *Tip*: you can specify a different name for the local directory. To create a local clone directory named "lab1" (omit the -spiderman) use:
  ```shell
  cmd> git clone https://classroom.github.com/prog2022/lab1-spiderman lab1
  ```
* Complete the assignment and test your code.
* Commit your work to Git.
  ```shell
  cmd> git status
  On branch master

  Changes not staged for commit:
      modified:  maze.py

  Untracked files:
      player.py

  cmd> git add maze.py player.py
  cmd> git commit -m "added player and finished quiz"
  cmd> git push
  ```

Ref: [Github Classroom videos](https://classroom.github.com/videos)

### Assignments using Your Own Account 

For some assignments you will create a repository in your personal account instead of Github Classroom.  In this case, create a repository in your Github account (the one you used to join our class) and push your work to it. 

Two things are important:

1. The Github repo name must **use the exact name** specified in the assignment.  Please be careful to use correct spelling and correct case of letters (upper/lowercase). If you use the wrong name, you might not get credit.
2. Make sure the Github repo is public or readable by instructor and TAs (if private).  Usually we will use public repos.

Example:
```
cmd>  cd /somepath/workspace/repo_name
# Create repository if necessary
cmd>  git init
cmd>  git add file1 file2 ..
cmd>  git commit -m "Add finished work"
# Add github repository (already created on Github) as a "remote"
cmd>  git remote add origin git@github.com:yourname/repo_name.git
# The first time you 'push' you must specify the remote and branch to use
cmd>  git push -u origin master
```
where `repo_name` is the remote repository (which you must create on github.com).

Note: By default, Github now calls the "master" branch "main". So you can write "main" instead of "master". I still prefer "master".

