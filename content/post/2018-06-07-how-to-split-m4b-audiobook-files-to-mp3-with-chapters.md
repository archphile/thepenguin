+++
title = "How to split m4b audiobook files to mp3 with chapters"
date =  "2018-06-07"
thumbnail = "/img/audiobook.jpg"
categories = ["Audio"]
tags = ["linux audio", "m4b", "ffmpeg", "m4b-tool"]
+++

Although [VLC](https://www.videolan.org/vlc/index.html) can perfectly hanlde **.m4b**  audiobook files, I usually prefer to **split them to mp3** in a way that each mp3 file is one chapter of the audiobook.

If you want to do do the same, I highly suggest you to use [m4b-tool](https://github.com/sandreas/m4b-tool). You can download the **.phar** file from the [GitHub releases page](https://github.com/sandreas/m4b-tool/releases).

This really nice tool requires [php](http://php.net/), [ffmpeg](https://www.ffmpeg.org/) and [mp4v2](https://code.google.com/archive/p/mp4v2/).

In order to install them in [Archlinux](https://archlinux.org), I gave the following command:

	pacman -S php ffmpeg libmp4v2
	
Now, let's assume that you have a file named **audiobook.m4b** and you want to split it. All you have to do is give the following command:

	php m4b-tool.phar split --audio-format mp3 --audio-bitrate 96k --audio-channels 1 --audio-samplerate 44100 /path/to/audiobook.m4b
	
The resulting **mp3 files** will be placed under a new directory named **audiobook_splitted**, on the same location with the **.m4b ** file, while each file name will be based on the following template:

	<chapter>-<chapter title>.mp3
	
ex.

	001-This is the first Chapter.mp3
	
	


