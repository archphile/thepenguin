+++
title = "DR14 T.meter - A tool to find the dynamic range of your music albums"
date = "2017-09-27"
thumbnail = "/img/loudness-war.jpg"
categories = ["Audio"]
tags = ["linux audio", "dynamic range", "DR14 T.meter"]
+++

[Dr14 T.meter](https://github.com/simon-r/dr14_t.meter) is an open source command line tool that computes the dynamic range of your music files.
It's a tool that I use in order to create reports for each of my FLAC albums I have in my music library.

Installing it in Archlinux was pretty easy:

	yaourt -S dr14_tmeter


In order to create a report for an album you need the following command:


	dr14_tmeter /path/to/album/


What is really nice about it is that you can use it recursively in order to create dynamic range repors 
for multiple albums at once:

	dr14_tmeter -r /path/to/album/library/


The result of these commands is a file within the album directory named **dr14.txt**. Here is an example
of such a file:

	﻿----------------------------------------------------------------------------------------------	
	 Analyzed: Vultures /  Artist: 1000mods
	----------------------------------------------------------------------------------------------	
	DR	Peak	RMS	Duration	Title [codec]	
	----------------------------------------------------------------------------------------------	
	 DR6	 -0.16 dB	 -6.83 dB	5:28	01 - Claws 	 [flac]	
	 DR6	 -0.13 dB	 -6.58 dB	3:46	02 - Big Beautiful 	 [flac]	
	 DR6	 -0.21 dB	 -8.06 dB	6:20	03 - She 	 [flac]	
	 DR7	 -0.23 dB	 -9.85 dB	3:24	04 - Horses' Green 	 [flac]	
	 DR7	 -0.23 dB	 -8.22 dB	4:19	05 - Low 	 [flac]	
	 DR6	 -0.22 dB	 -8.33 dB	5:03	06 - Vultures 	 [flac]	
	 DR6	 -0.18 dB	 -7.57 dB	2:54	07 - Modesty 	 [flac]	
	 DR7	 -0.19 dB	 -9.03 dB	6:42	08 - Reverb Of The New World 	 [flac]	
	----------------------------------------------------------------------------------------------	
	 Number of files:    8
	 Official DR value:  DR6
		
	 Sampling rate: 		 44100 Hz
	 Average bitrate: 		 894kbs 
	 Bits per sample: 		 16 bit
		
	Dr14 T.meter 1.0.16 
	==============================================================================================	






 
