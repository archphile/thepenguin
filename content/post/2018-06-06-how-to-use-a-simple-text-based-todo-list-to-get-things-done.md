+++
title = "How to use a simple text based to-do list to get things done"
date = "2018-06-06"
thumbnail = "/img/todotxt.jpg"
categories = ["General"]
tags = ["todotxt", "dropbox", "simpletask", "qtodotxt", "todotxt-machine", "gtd"]
+++

After testing almost every available tool in order to create and maintain my to-do lists, I decided I needed something that followed the **k.i.s.s.** software philosophy and this is the reason I started using [Taskwarrior](https://taskwarrior.org/).

[Taskwarrior](https://taskwarrior.org/) has  all the advantages of a text based to-do list application, but with two drawbacks for me:

- I didn't like the **unofficial** Android application (very important for me)
- I needed to have a VPS  running [taskd](https://taskwarrior.org/docs/taskserver/configure.html)  in order to be able to sync my PC and smartphone

After using [Taskwarrior](https://taskwarrior.org/) for about two months, I went back to what I new best: using a  paper to-do list!

That was the proof that I had failed to find the right tool for me and I had to keep searching.

That was when I found [todotxt.org](http://todotxt.org/). This website has all the information needed in order to create and maintain a simple **todo.txt** list, suggesting [a set of formatting rules](https://github.com/todotxt/todo.txt)  to make this procedure easier and, the most important, **standardized**. 

Lets have a look at a summary of the rules:

![todo.txt rules](/img/todotxt-rules.png "todotxt")

and lets say that I want to keep a note to make [myMPD] ({{< ref "2018-06-04-mympd-my-new-favorite-mpd-client" >}}) packages for [Archphile](http://archphile.org) . That would be:

	create myMPD packages for archphile
 
 Let's start adding information:
 
	2018-06-06 create myMPD packages for +archphile
 	
 
 What I just did, apart from **adding the creation date**, was to identify archphile as a **project** tag (adding the **+**  before the word).
 
 
Let's add some more stuff:
 
	(C) 2018-06-06 create myMPD packages for +archphile @pc due:2018-06-08
 	
 This is a more complete approach on how to keep a task on that list. It includes a **context** tag (which is the **pc** - using the  @ before the word) plus a **due date** at the end. The **(C)** in the beginning means that this task is of a not a high  priority (that would be A or B for example - however you will decide what these priorities mean).
 
 So, all I have to do is to just write this line on my **todo.txt** file.
 
 Now lets assume that I finally created the packages one day later than expected. All I have to do is **edit todo.txt**  using **any text editor I want** and modify the line:
 
	x (A) 2018-06-09 2018-06-06 create myMPD packages for +archphile @pc due:2018-06-08
 	
 The **x in the beginning** of the line means that this task is done and the day just before the creation date is the day that this task was actually done.
 
Another valid alternative for the above, is the following, with the only difference being the order of completion date and priority:

	x 2018-06-09 (A) 2018-06-06 create myMPD packages for +archphile @pc due:2018-06-08

All the instructions above are the fundamentals of this **todo.txt** approach. 

You can stop reading this article  and start using your file with a text editor, but below you 'll find some interesting ways of maintaining  **todo.txt** with the use of various programs.

&nbsp;
### The todo.sh script

[todo.sh](https://github.com/todotxt/todo.txt-cli/releases) script is one of the oldest applications (initially created by [Gina Trapani](https://ginatrapani.org/)) you can use to maintain **todo.txt** file. In order to install it in [Archlinux](https://archlinux.org), I got it from [AUR](https://aur.archlinux.org/):

	yaourt -S todotxt
	
the next step was to copy the sample config to my **home**:

	cp /usr/share/todotxt/todo.cfg /home/satan/.todo/config

Finally I needed to edit this file and set the location of my **todo.txt** file:

	export TODO_DIR="/home/satan/Dropbox/todo"

**Note:** as you can see I am using [Dropbox](https://www.dropbox.com/) to store the file, but I will come back on that later.
&nbsp;

The basic use of **todo.sh** is very easy:

To put a new task you need to do it like in this example:

	todo.sh add "(C) 2018-06-06 create myMPD packages for +archphile @pc due:2018-06-08"
	
To see all tasks:

	todo.sh list
	
the output should be similar to the one below:

	1 (C) 2018-06-06 create myMPD packages for +archphile @pc due:2018-06-08
	2 2018-06-06 add todo.txt article on +thepenguin @pc due:2018-09-06
	3 buy new keyboard +shopping @pc

To set the first task as done (and archivr it to **done.txt**):

	todo.sh do 1

To give priority A to task 3:

	todo.sh pri A 3
	
To remove priority  from task 3
		
	todo.sh depri 3
	

In order to see **todo.sh** in action, I highly recommend you to see [this video](https://vimeo.com/3263629).

What [Gina Trapani](https://ginatrapani.org/) suggests on this tutorial, is the use of a very short alias, that indeed makes life easier:

	alias t='todo.sh'
	
If you follow this tip, you won't have to type **todo.sh** again. So in order to ex. add a new task:

	t add "this is a task +koko @lala"

&nbsp;
#### todo.sh addons

There are [plenty of community add ons](https://github.com/todotxt/todo.txt-cli/wiki/Todo.sh-Add-on-Directory)  for **todo.sh** script. I haven't spent much time on testing them. 

The only one I have currently installed is [due](https://github.com/rebeccamorgan/due). In order to get it, I did the following:

	mkdir ~/.todo.actions.d
	cd ~/.todo.actions.d
	git clone https://github.com/rebeccamorgan/due.git
	chmod +x ~/.todo.actions.d/due/due
	
Using it with like below:

	todo.sh due

I am able to list by due date (by default tasks that are due today or tomorrow)

Adding an extra option, ex:

	todo.sh due 9

I am able to list by due date, showing due today plus tasks for the next 8 days (8+1)

&nbsp;
### The todotxt-machine cli application

[todotxt-machine](https://github.com/AnthonyDiGirolamo/todotxt-machine)  is a really nice application that uses **todo.sh** and offers a nice cli interface:

In order to install it, I got it from [AUR](https://aur.archlinux.org/):

	yaourt -S todotxt-machine-git
	
Then, in order to use it I created the following bash alias:

	alias mytodo='todotxt-machine /home/satan/Dropbox/todo/todo.txt /home/satan/Dropbox/todo/done.txt'
	
**Note:** **done.txt** is the file  where the completed tasks are written on when they are removed from **todo.txt**.

This is a nice demo of how this program looks like:

![todotxt-machine interface](/img/todotxtmachine.gif "todotxt-machine")

**Note:** I created a **pdf** that includes all **todotxt-machine** keyboard **bindings**. You can download it [here](http://thepenguin.eu/download/todotxt-machine-keys.pdf). 

&nbsp;
### Simpletask application on Android

[Simpletask](https://github.com/mpcjanssen/simpletask-android) is the reason that i finally kept using **todo.txt**, as with this application I am able to:

- sync my PC with my smartphone
- use a simple and clean interface in order to update my to-do list
- sort my list and view by project or context (or both) very easily

[Simpletask](https://github.com/mpcjanssen/simpletask-android) offers three alternative options:

- An app that syncs with [Dropbox](https://www.dropbox.com/) 
- An app that syncs with [Nextcloud](https://nextcloud.com) 
- An app that does not sync

This is the main view of [Simpletask](https://github.com/mpcjanssen/simpletask-android):

![simpletask interface](/img/simpletask.jpg "simpletask")

At the moment I don't have any self hosted [Nextcloud](https://nextcloud.com)  server, so I am using [Dropbox](https://www.dropbox.com/)  (only for the todo.txt file), but I am about to move to a [Nextcloud](https://nextcloud.com) server very soon, because I really don't trust to use proprietary applications to store my data.

**Note:** For a better **GTD** experience, please make sure that you select "USe todo.txt terms" ins Simpletask setting.

&nbsp;
### Qtodotxt GUI application for Linux/Win/OSX

[Qtodotxt](https://github.com/QTodoTxt/QTodoTxt) is a very nice GUI application for those who don't want to mess around with terminal.

![qtodotxt interface](/img/qtodotxt.jpg "qtodotxt")

The only issue I've found with this is that there's a bug that prevents "created date" to be automatically added.


&nbsp;
### Summary:

Using **todo.txt** and editing this file with various tools (mainly with [Simpletask](https://github.com/mpcjanssen/simpletask-android) because it's an **amazing app** and with **todo.sh** when I want to quickly add a new task from the PC ) has been a real pleasure for me. I believe that it's by far **the easiest way** to maintain a to-do list and  **get things done**.

With a **todo.txt** file you forget about proprietary solutions and ensure that you will be able to read your to-do list **forever!**

**Notes:** 

- Apart from all the installation guides etc., the most important part of this procedure is to [read about](https://github.com/todotxt/todo.txt)  and understand **projects** and **contexts**. These terms were initially described in **David Allen's** book [Getting Things Done](https://en.wikipedia.org/wiki/Getting_Things_Done). It's a good idea to spend some time and google about it so that you have a better understanding on **GTD**. 

- Use a due date only for tasks that **must be done**  and **not** f or tasks that you **want to be done**. Try to familiarize yourself with priorities instead!
