---
title: About
navigation_order: 4
---

## About the Course

| **Time** | Lecture Tues 9:00-12:00, Lab Thurs 9:00-12:00 beginning 11 Jan
| -------------|--------------------------------------------------------
| **Location** | Meet **online** using [Google Classroom][google-classroom] and [Google Meet][google-meet]. Class code: **uheeiyq**
| **Github** | We use [Github](https://github.com) for programming work, so you must have a Github account. 
| **Schedule & Assignments** | Weekly Schedule is on [Google Classroom][google-classroom-classwork].
| **Discord** | For Q&A, discussions, meetings <https://discord.gg/JZrgpJNb>
| **Scores** | <https://bit.ly/PROG2022-scores> for classwork and homework 

[google-classroom]: https://classroom.google.com/c/NDUxMTk5MjA4OTk0
[google-classroom-classwork]: https://classroom.google.com/w/NDUxMTk5MjA4OTk0/t/all
[google-meet]: https://meet.google.com/oco-cbri-gzu


### How to Join [Google Classroom][google-classroom-link] and Join a Meeting

1. Join the [Google Classroom](https://classroom.google.com).  Use class code **[ka25cph][google-classroom-link]** or click this **[invitation link][google-classroom-link]**.
2. To join a meeting, click on the "Meet" link (video icon) on the Google Classroom page:
[![classroom meet icon](images/classroom-meet-icon.png)][google-meet-link]
   - You can also click this [Google Meet Link][google-meet-link] but it may change in the future.
3. Complete this [Student Info Form](https://forms.gle/WE3jN4miDKabFBje8) so we know your Github ID.
4. What online platform do you prefer? Please complete [Online Platform Preferences](https://forms.gle/VkG5MBPjgmxRX1xi7).


### [Introduction to the Course](introduction/index)
(click the above link for Intro)

### Instructors

[James Brucker](https://github.com/jbrucker) 

Chaiporn Jaikaew `email("Chaiporn", "Jaikaew")`

Piyamate Wisanuvej `email("Piyamate", "Visanuvej")`

### Teaching Assistants (TAs)

[Poomtum](https://github.com/TopsonArcana) `email("Poomtum","Rattanarat")`

[Thanatibordee](https://github.com/ParnThanatibordee) `email("Thanatibordee","Sihaboonthong")` 	

[Vitvara](https://github.com/vitvara) `email("Vitvara","Varavithya")`


```python
DOMAIN = "ku.th"

def email(firstname: str, lastname: str, nlast: int = 1) -> str:
    """Return the email address for a KU person."""
    # \u0040 is Unicode for 'at' symbol
    return f"{firstname}.{lastname[0:nlast]}\u0040{DOMAIN}"
```

*Why obfuscate email addresses?*    

Software "bots" constantly scan the web for email addresses 
and use them to send spam and phishing attacks.
Some people disguise their email as "santaclaus at christmas dot com",
but that is easily recognized by pattern matching.
