+++
title = "How to create spectrograms for audio files using sox"
date = "2017-09-27"
thumbnail = "/img/spectro.jpg"
categories = ["Audio"]
tags = ["linux audio", "spectrogram", "sox"]
+++

The use of spectrograms is one of the most accurate procedures in order to identify the quality of audio files.
Let's say that you were given an music album with 16/44.1 flacs and you want to see if the files included are actually redbook. 

One of the best tools I've found for that is [sox](http://sox.sourceforge.net/SoX/Resampling).

The installation in Archlinux is the following:


	 pacman -S libsoxr


In order to create a spectrogram for a specific flac file, you need the following command:


	sox blabla.flac -n spectrogram -o blabla.png


Now, lets see a quicker procedure in order to create a set of spectrograms for the whole album with the following script:


	#!/bin/bash
	mkdir -p spectrograms
	for file in *.flac;do
	    outfile="${file%.*}.png"
	    sox "$file" -n spectrogram -o "$outfile"
	    mv "$outfile" spectrograms/
	done
	mogrify -strip -quality 80% -sampling-factor 4:4:4 -format jpg spectrograms/*.png
	rm /spectrograms/*.png

This script must be run within the album directory. It creates a directory named **spectrograms**  and places the **.png** files inside. Then, **mogrify** converts the png to  
much smaller **.jgp** images and finally the un-needed png files get deleted.Now we have a directory that includes all spectrograms for our files while it's size is really 
small and we can keep the spectros for all our music library.

Below you can see a sample of the final image, showing the spectrogram of a redbook (16/44.1) flac:




![dr14 T.meter](/img/spectro-sox.jpg)"}