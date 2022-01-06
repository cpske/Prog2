---
title: Introduction to the Course
---

This course covers 

1. Object-oriented design and programming, including some design patterns
2. Functional programming 
3. Guidelines for writing good quality code
4. Graphical applications and graphical user interfaces using Tkinter
5. Data exploration and scientific programming using Jupyter Notebooks


### Course Objectives (What You Will Hopefully Learn)

Learn to design, implement, and test applications with several components. Learn how to use libraries or frameworks to build on existing code, and to manage your code and project documents in a version control system; in particular, be able to use git and Github.

You should be able to use API documents to find information, and not rely on searching for solutions on StackOverflow.  You should also be able to write good documentation for your own code, using a standard format (Javadoc) and documentation generator.

You should learn guidelines for writing good quality code, 
including a coding convention and coding standard, 
and design principles and patterns to help you design good software.

### Requirements 

Students need to commit several hours per week to read, study, and do assignments on their own.

Everyone is required to do the assigned work **individually**.  Please do not ask other students to "teach" you or copy work from anyone else.
If you need help, please ask the TAs or instructors.

### Coursework

1. 

### Topics

The topics are listed on the [topics page](../index). 

### Online Course Material 


### Resources






### Requirement for Individual Work

All assignments *must* be done **individually**, unless group work is explicitly allowed.

It is OK to discuss an approach to solving a problem, but not to share code.  If you need help, please ask the TAs or instructors rather than the other students (who may not give you the correct answer).

### Copying == Fail

Anyone who submits **any** copied work will receive grade "F" and be reported to Faculty of Engineering for disciplinary action.

### Course Work & Grading

Your grade is based on:

* written exams 
* programming exams
* programming assignments
* quizzes
* homework
* class participation
* lab participation and lab work

**Minimum Exam Score:** To pass the course you must have an **average exam score at least 50%**.

If you achieve the minimum exam score, then the following grading scale is used based on your overall work:

| Overall | Grade |
|---------|-------|
|  > 85%  |   A   |
| 75-85   |   B   |
| 65-75   |   C   |
| 55-65   |   D   |
|  < 55%  |   F   |

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

Your Github ID is `spiderman` and the assignment url is http://bit.ly/quiz1.

* Visit http://bit.ly/quiz1 and accept the assignment.
* Refresh the page. It shows your repo url is:
  ```
  https://classroom.github.com/prog2022/quiz1-spiderman
  ```
* Click on the link to visit the repo, so you can see the files and formated README.
* Clone the repository to your computer. Using the ancient command line:
  ```shell
  # change to a directory where you store programming work
  cmd> cd /somepath/prog2/workspace
  cmd> git clone https://classroom.github.com/prog2022/quiz1-spiderman
  ```
  This will create a local directory named `quiz1-spiderman` containing your work.    
  Tip: you can specify a different name for the local directory. To create a local clone directory named "quiz1" (omit the -spiderman) use:
  ```shell
  cmd> git clone https://classroom.github.com/prog2022/quiz1-spiderman quiz1
  ```
* Complete the quiz and test your code.
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

Some assignments don't use Github Classroom.  In this case, create a repository in your Github account (the one you used to join our class) and push your work to it. 

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


## Prerequisite Knowledge

You need to know:

1. Everything that was covered in Programming 1, including methods, loops, conditional expressions, arrays and ArrayList, defining classes, and creating objects. 
  * How to write and compile Java, including creating and using objects.
2. How to use the command line on your computer, including these commands:
  * How to display name of the current directory.
  * How to change directory.
  * How to list all the files in a directory.
  * How to copy, move, or rename a file.
  * How to delete a file.
3. Where (what directory) is the Java SDK installed on your computer?
4. How to use an IDE such as Eclipse, IntelliJ, or Netbeans.
5. How to use Git and Github.
  * Create a new local repository
  * Add files to the repository
  * Remove (delete) files in the repository
  * Check status of your repository
  * Add Github as a "remote" repository
  * Copy your local repository to Github ("push")
  * Create a local repository as a "clone" of a Github repository

---
[skeoop.github.io]: https://skeoop.github.io
[google-classroom]: https://classroom.google.com
[resources]: https://skeoop.github.io/Resources
[github-oop2018]: https://github.com/OOP2018
[github-classroom]: https://classroom.github.com/classrooms/32051939-ske-programming-2
