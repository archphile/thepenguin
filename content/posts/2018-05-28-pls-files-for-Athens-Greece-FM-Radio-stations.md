+++
title = "pls files for Athens (Greece) FM Radio stations"
date = "2018-05-28"
thumbnail = "/img/webradio.jpg"
categories = ["Audio"]
tags = ["webradio", "archphile", "greece"]
+++

This post is about something I wanted to create for years: a complete **.pls** set for **Athens (Greece) FM Radios**.
Two months ago I found a very interesting [m3u file](https://gist.github.com/dennmtr/ac14e66adca47e5f7d60) (by [dennmtr](https://github.com/dennmtr)) on which I based my work and created the following GitHub repository:

[https://github.com/archphile/AthensFMRadios](https://github.com/archphile/AthensFMRadios)


I tried to include almost every FM Radio station I found online. If you didn't find a station you want, this means:

1. I forgot it
2. I did not find a usable http stream (ex. SKAI 100.3)
3. It's a religious radio station

For 1 and 2 and in cases where an existing pls is not functional, feel free to open issues, fork and send me back, etc..

For 3, please go away from my blog  immediately or I will use my dark unholy skills to destroy you.. Seriously!

### How to use these pls files with Archphile

Its' pretty easy! I have created a very small script that does the job. All you have to do is the following (the first command starts from wget and ends at /arf.sh):

	wget https://raw.githubusercontent.com/archphile/AthensFMRadios/master/archphile-script/arf.sh

	chmod +x arf.sh

	./arf.sh

	mpc update

This script will delete the existing files and download the latest ones from GitHub.

**EDIT:** **0.99.73** is missing **unzip** which is required by **arf** script. In order to install unzip, edit mirrorlist:

	nano /etc/pacman.d/mirrorlist
	
enable the first server line, save and then install unzip command:

	pacman -Sy unzip
	
Now you are ready to follow the initial procedure.


**Note 1:** It's obvious that most of these web radios are garbage. Use at your own risk!

**Note 2:** These files were **created for real people** that want to listen to the radio and not for "audiophiles" (who gives a fuck about them anyway?)! 

**Note 3:** Apart from Archphile, these files can be used with almost any other player out there. 



