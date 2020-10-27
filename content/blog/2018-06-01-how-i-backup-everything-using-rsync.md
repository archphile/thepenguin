+++
title = "How I backup everything using Rsync"
date = "2018-06-01"
thumbnail = "/img/rsync.jpg"
categories = ["Linux DIY"]
tags = ["backup", "rsync", "nas", "usb disk"]
+++

Further to my posts [part I]({{< ref "2018-05-30-a-poors-man-diy-usb-nas-part-1.md" >}}) and [part II]({{< ref "2018-05-31-a-poors-man-diy-usb-nas-part-2.md" >}}) about my DIY USB NAS, I am writing this one in order to show you how easy it is to get various backups with [rsync](https://en.wikipedia.org/wiki/Rsync).

But first let me explain you how I store my data:

**Desktop PC hard disk (WD Black 1T)**

This is the disk that stores my Linux **home**. This is also the **primary location** of my **music** and **pictures**.

**DIY USB NAS (with a WD Red 3T)**

This storage has a complete backup of my home, plus some other stuff I keep there as a primary location (photography webinars, stuff about my job, series etc.. - I don't want all this stuff on my home drive). 

I use many samba shares (one for music, another for pictures, a third for webinars etc..) in order to divide all these data so that it will be easier for me to **choose which one to backup** etc.. 

**USB WD Mybook 2T**

This is an old WD my book disk that I use in order to **backup the important data from my NAS**.This disk is **kept at a different location** and I bring it home once a month, only to get the NAS backup.


**To sum up:**

For the data I really care (**music**, **pictures** and my Linux **home** files)  I have **three copies**:

1. on the hard disk of my desktop PC
2. on my NAS
3. on the disk (Mybook) that keeps the NAS backup


For the data I care less (ex. my collection of webinars) I have **two copies**:

1. on my NAS
2. on the disk (Mybook) that keeps the NAS backup

For the data I don't care (movies, series etc..), I have **one copy**:

1. on my NAS

But let's see what I do in order to backup them.

## Rsync commands

In order to backup my music (and everytime I want to add an album on the MPD library - [Archphile](http://archphile.org)  only sees my NAS), I use the following command:

	rsync --progress --stats -r -l -D --update --delete-after /home/satan/Music/ /mnt/ddwrt/music/
	
In order to backup my pictures I use a similar command:

	rsync --progress --stats -r -l -D --update --delete-after /home/satan/Pictures/ /mnt/ddwrt/images/'
	
For the rest of my home data I use the following command (with different options to preserve ownership, permissions, etc..):

	rsync --progress --stats -Dgloprtg --update --delete-after --exclude ".local/share/Trash" --exclude "/.cache" --exclude "/Music" --exclude "/Pictures" /home/satan/ /mnt/ddwrt/backup/
	
For these three commands, I use **aliases in .bashrc**. In order to take these backups, I just type **syncmusic**, **syncpic** or **synchome**.

All three commands are run very frequently, so that the NAS has fresh copies of my data.

**Once a month,** I bring the third disk (Mybook) at home and get the NAS backup with the following script in order to choose what I want to backup:

	#!/bin/bash

	rsync --progress --stats -r -l -D --update --delete-after /mnt/ddwrt/music/ /run/media/satan/backup_1/music/
	rsync --progress --stats -r -l -D --update --delete-after /mnt/ddwrt/pictures/ /run/media/satan/backup_1/pictures/
	rsync --progress --stats -r -l -D --update --delete-after /mnt/ddwrt/photography/ /run/media/satan/backup_1/photography/	
	rsync --progress --stats -r -l -D --update --delete-after /mnt/ddwrt/job/ /run/media/satan/backup_1/job/
	rsync --progress --stats -r -l -D --update --delete-after /mnt/ddwrt/tun/ /run/media/satan/backup_1/tun/
	rsync --progress --stats  -Dgloprtg --update --delete-after /mnt/ddwrt/backup/ /run/media/mikes/backup_1/backup/
 
The flexibility of this very easy script, is that I choose what to backup from the NAS and this is how I exclude everything I don't care about (ex. my series).

## Summary

- I have been using this procedure for more than one year with great success. 

- Having the bad habit of shift+delete and keeping my home on my NAS has really saved me many times.

- I could use a **cron** for synchome, syncmusic and syncpic, but my NAS is not always up, so I prefer doing it manually.

