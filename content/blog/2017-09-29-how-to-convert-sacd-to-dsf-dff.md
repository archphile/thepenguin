+++
title = "How to convert SACD ISO to dsf/dff files"
date =  "2017-09-29"
thumbnail = "/img/sacd.jpg"
categories = ["Audio"]
tags = ["linux audio", "sacd", "dsd"]
+++

SACD ISO support is not a popular feature in media players, especially when it comes to Linux audio.

As of today the most popular solution is an [MPD fork](http://git.musicpd.org/cgit/manisiutkin/mpd.git), a program not found by default in most of the Linux distributions (if you have an [Archphile](http://archphile.org) supported board however you can use the package I have created for that).

If you have this type of files and you can't currently use them, the best solution is to convert them to separate **.dsf** or **.dff** files.

Below I will show you one command line and one GUI option (that uses the same command line tool).

## Command Line Procedure

In order to proceed you will need [sacd-ripper](https://sourceforge.net/projects/sacd-ripper/).

I am an Archlinux user so all I had to do was to give the following command:

	yaourt -S sacd-extract

the man page of this tool is pretty straight-forward:

	The following options are available for the sacd_extract commandline tool:
	
	Usage: sacd_extract [options] [outfile]
	  -2, --2ch-tracks                : Export two channel tracks (default)
	  -m, --mch-tracks                : Export multi-channel tracks
	  -e, --output-dsdiff-em          : output as Philips DSDIFF (Edit Master) file
	  -p, --output-dsdiff             : output as Philips DSDIFF file
	  -s, --output-dsf                : output as Sony DSF file
	  -I, --output-iso                : output as RAW ISO
	  -c, --convert-dst               : convert DST to DSD
	  -C, --export-cue                : Export a CUE Sheet
	  -i, --input[=FILE]              : set source and determine if "iso" image,
	                                    device or server (ex. -i192.168.1.10:2002)
	  -P, --print                     : display disc and track information
	
	Help options:
	  -?, --help                      : Show this help message
	  --usage                         : Display brief usage message
	

Based on the above, the command you will need is the following:

	sacd_extract -2 -s -C -i blabla.iso


## GUI Procedure

In order to get the GUI, you need to visit [this link](http://www.audiocircle.com/index.php?topic=129913.0)  and download is2dsd. This program is in fact nothing more than a **java gui** of sacd-ripper.

Make sure that you have java installed and run it. You will see something similar to the image below:

![iso2dsd](/img/iso2dsd.jpg  "iso2dsd")

All you have to do is to load the **.iso**. If you want to extract the stereo version of the SACD in **.dsf** format (it's the best option as it supports tags) and you want to create a **.cue** file, make sure your settings are identical to the image above. 

As a last step, press the **Execute** button, wait for the procedure to finish and thats all. Your **.dsf** files are ready!




	


