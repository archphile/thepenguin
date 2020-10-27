+++
title = "How to create spectrograms for audio files using sox"
date = "2017-09-27"
thumbnail = "/img/spectro.jpg"
categories = ["Audio"]
tags = ["linux audio", "spectrogram", "sox"]
+++

Using spectrograms is one of the most accurate procedures in order to identify the quality of audio files.
Let's say that you were given an music album with 16/44.1 flacs and you want to check wether the files included are "redbooks" or not. 

One of the best tools I've found for this procedure is [sox](http://sox.sourceforge.net/SoX/Resampling).

To install it under Archlinux, just give the following:


	 pacman -S libsoxr


In order to create a spectrogram for a specific flac file, you need to give the following command:


	sox blabla.flac -n spectrogram -o blabla.png


Now, lets see a quicker procedure in order to create a set of spectrograms for the whole album with the help of a simple bash script:


	#!/bin/bash
	mkdir -p spectrograms
	for file in *.flac;do
	    outfile="${file%.*}.png"
	    sox "$file" -n spectrogram -o "$outfile"
	    mv "$outfile" spectrograms/
	done
	mogrify -strip -quality 80% -sampling-factor 4:4:4 -format jpg spectrograms/*.png
	rm /spectrograms/*.png

This script must be run within the album directory. It creates a directory named **spectrograms**  where it stores the **.png** files. Then, **mogrify** converts the png to  
much smaller **.jpg** images and finally the un-needed png files get deleted. 

Now we have a directory that includes all spectrograms for our files. Their size is really small and we can keep the spectros for all our music library.

Below you can see a sample of the final image, showing the spectrogram of a redbook (16/44.1) flac:




![dr14 T.meter](/img/spectro-sox.jpg)