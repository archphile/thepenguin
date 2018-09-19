+++
title = "Understanding the use of DSD files with MPD"
date = "2017-12-22"
thumbnail = "/img/dsd.jpg"
categories = ["Audio"]
tags = ["linux audio", "dsd", "mpd"]
+++

DSD, although a very old and failed technology, is again one of the hottest trends in computer audio. Below you will find a quick guide for [MPD](https://www.musicpd.org) (Music Player Daemon) that will cover most of your needs:
&nbsp;
### MPD and DSD with DoP
&nbsp;
Assuming that your DAC supports the **DoP** protocol, the only you need to do is to add the following line in **audio_output** section of **mpd.conf**:

	dop       "yes"

Below you can see an example of this section:

	audio_output {
	enabled         "yes"
	type            "alsa"
	name            "Aune S16"
	device          "hw:1,0"
	auto_resample   "no"
	auto_channels   "no"
	auto_format     "no"
	dop             "yes"
	}
	

Then you just need to restart MPD

	systemctl restart mpd

To double-check that everything is ok, you can start listening to ex. a **DSD 64** file, and test with the following command:

	cat /proc/asound/card*/pcm*p/sub*/hw_params

The output is:

	closed
	access: RW_INTERLEAVED
	format: S24_LE
	subformat: STD
	channels: 2
	rate: 176400 (176400/1)
	period_size: 22050
	buffer_size: 88200

**DoP** uses **PCM** and this is the reason that the format is **S24_LE**  and the sampling rate is **176400**. 

&nbsp;
### MPD and Native DSD
&nbsp;
Native DSD is a little bit more complicated. IF the DAC supports DSD and if the Linux Kernel supports your DAC in Native DSD mode, the only thing you need to do is remove the dop option from **audio_output** section of **mpd.conf**

Below you can see an example of this section:

	audio_output {
	enabled         "yes"
	type            "alsa"
	name            "DiyinHK 9018k2m"
	device          "hw:1,0"
	auto_resample   "no"
	auto_channels   "no"
	auto_format     "no"
	}

If everything is ok, then you will see the following output if you run the test command while listening to a **DSD 64** file:

	cat /proc/asound/card*/pcm*p/sub*/hw_params

	closed
	access: RW_INTERLEAVED
	format: DSD_U32_BE
	subformat: STD
	channels: 2
	rate: 88200 (88200/1)
	period_size: 11025
	buffer_size: 44100

The format now has changed and it's **DSD_U32_BE** and the sampling rate is **88200**.


If your DAC does not support Native DSD (like my Aune S16 below) or if it supports but Linux Kernel isn't, when you remove the DoP option, MPD converts DSD to PCM on the fly and the test command has an output similar to the one below:

	access: RW_INTERLEAVED
	format: S32_LE
	subformat: STD
	channels: 2
	rate: 352800 (352800/1)
	period_size: 32768
	buffer_size: 131072 

The format is PCM again (**S32_LE**) and the sampling rate is the maximum the receiver and DAC support, **352800**.

In gerneral, **Native DSD** support is limited, so if your DAC supports DoP, this is the best way to listen to your DSD files at the moment. DoP is an old and mature protocol and has no audible differences when compared to Native DSD.

If you want to have a look at Linux kernel code and see the supported Native DSD devices, you can follow the link below:

[https://github.com/torvalds/linux/blob/master/sound/usb/quirks.c](https://github.com/torvalds/linux/blob/master/sound/usb/quirks.c) 

Please note that every Linux distro uses a different version of Linux kernel. In addition, if you use an embedded board like Raspberry Pi, Odroid, Udoo, you usually don't use the mainline kernel and in many cases your version is very old.

&nbsp;
### MPD and SACD ISO support
&nbsp;
Although MPD does not officially support **SACD ISO** files, thanks to an **MPD fork** this option became available for MPD users. 

What you need to do is build this fork (or ask your distribution for this package). The source code can be found in this location:

[https://sourceforge.net/projects/mpd.sacddecoder.p/](https://sourceforge.net/projects/mpd.sacddecoder.p/)

This fork is almost identical to MPD apart from the SACD code. You need to edit mpd.conf and put some additional stuff:

	decoder {
	plugin "sacdiso"
	dstdec_threads "4"
	edited_master "true"
	lsbitfirst "false"
	playable_area "stereo"
	}


	decoder {
	plugin "dvdaiso"
	no_downmixes "false"
	no_short_tracks "false"
	playable_area "multichannel"
	tags_path "/var/lib/mpd/dvda_metabase"
	tags_with_iso "true"
	}

The first section is for **SACD ISO** and the second for **DVD ISO** (I have never tested DVD ISO to be honest). Please note that you will have to modify for your needs.

Please note again that if you are using this fork this means that **you are not using official MPD**, so if you have a problem and you need help you should always mention this in forum posts, bug reports etc.

&nbsp;
### Notes and random thoughts

- MPD is a really nice piece of software with very active development. It's always a good idea to use the latest available version.

- If you don't use latest MPD or if you use the SACD **MPD fork**, don't ask for help in musicpd forum. It's a really bad idea!

- Many DACS have isssues with **DSD silence** and the result is ugly noises when changing tracks, play or pause,etc.. This is not a problem of MPD anymore (it used to be in the past but now it uses the correct DSD silence pattern). My Aune S16 is still very noisy while my DIY 9018K2m with Diyinhk XMOS is completely silent.

- If you compare DSD with PCM, even with the same album and you find DSD or PCM superior, please note that you might comparing [different masters]({{ site.baseurl }}{% post_url 2017-10-04-comparison-between-cd-and-vinyl-masters%})! If the sound quality of DSD is better it doesn't mean that the format is better.

- If your DAC does not support DSD don't get mad. The music you will find in DSD format is very limited and it's usually Classic Rock, Jazz and Classical. Just use PCM as 99.99% of people do!

- If you have a **Raspberry Pi 3** or an **Odroid C2** you can use my distro named [Archphile](http://archphile.org) that includes everything mentioned in this post!
