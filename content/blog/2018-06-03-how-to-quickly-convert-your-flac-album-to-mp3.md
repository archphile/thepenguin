+++
title = "How to quickly convert your FLAC album to mp3 with whatmp3"
date =  "2018-06-03"
thumbnail = "/img/lame.jpg"
categories = ["Audio"]
tags = ["linux audio", "flac", "mp3", "whatmp3"]
+++

Even though all my music library is 99,99% flacs, there are times when I need a quick **.flac to .mp3** conversion (for example to put music on the smartphone for running purposes).

The best and tool I have found so far, is [whatmp3](https://github.com/RecursiveForest/whatmp3), that uses [lame](http://lame.sourceforge.net/) to do the conversion.

In order to install it in Archlinux, I got it from [AUR](https://aur.archlinux.org/):

	yaourt -S whatmp3
	

As a last step, I (re-)installed lame :

	pacman -S lame
	
	

The use of **whatmp3** is pretty easy:

	whatmp3 --320 your_flac_album_dir
	
or even better:

	whatmp3 --V0 your_flac_album_dir


and after a while, the new directory with the mp3 files will be ready to use!


All supported mp3 qualities are:

	--320                 convert to 320
	--V0                  convert to V0
	--V2                  convert to V2
	--V8                  convert to V8
	--Q8                  convert to Q8


but I always use V0 (for various reasons that will be explained in another post).


What is really nice about **whatmp3**, is that it respects the directory naming scheme I use. 

All my FLAC directories are like the one below:

	Artist - Album (year) [FLAC] {Release Information}

When **whatmp3** finishes with the **V0** conversion of this album, the output directory is automatically named:

	Artist - Album (year) [V0] {Release Information}


**Note:** whatmp3 can do many more than a FLAC to mp3 conversion. Just install and type:

	whatmp3 --help

to see what you can do with this nice tool!