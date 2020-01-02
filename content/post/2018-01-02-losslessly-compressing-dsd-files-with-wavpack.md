+++
title = "Losslessly Compressing DSD files with Wavpack"
date = "2018-01-02"
thumbnail = "/img/wavpack.jpg"
categories = ["Audio"]
tags = ["linux audio", "dsd", "mpd", "wavpack"]
+++

One of the biggest disadvantages of **DSD** files is their size. Most of the users who like DSD format, keep large [SACD ISOs] ({{< ref "2017-09-29-how-to-convert-sacd-to-dsf-dff.md" >}})
or split them to **dsf/dff** files. In both cases, the result is horrible space-wise as the majority of music albums need more than **1.5GB** (only for the 2 channel files).

It was not long ago that [Wavpack](http://www.wavpack.com) project came with a solution to the above: a **lossless compression algorithm** for dsf/dff files, resulting in up to **60% smaller files**.

In order to test it, I quickly installed wavpack:

	pacman -Sy wavpack

and chose a **SACD ISO** file for my test. The size of the ISO was **3.5GB**. After the exctraction of **2 channel dsf files** (who needs 5.1?!?), the total size was **2.6GB**.

The next step was the wavpack compression. Reading the man page of wavpack command, I noticed some interesting options:

     -d
           delete source file if successful (use with caution!)

       -f
           fast mode (fast, but some compromise in compression ratio)

       -h
           high quality (better compression ratio, but slower encode and decode than default mode)

       -hh
           very high quality (best compression, but slowest and NOT recommended for use on portable
           playback devices)

       --import-id3
           import applicable tag items from ID3v2.3 tag present in DSF files into APEv2 tag (if there
           are > 1 MB cover images present add --allow-huge-tags to include them, and -r if you do not
           want large images appearing twice in the WavPack file, although this will remove the entire
           ID3 tag wrapper)

The first test I did was very basic and with standard compression:

	wavpack *.dsf

The resulting **.wv** DSD files had a total size of **1.6GB**.


Now it was time to test the **high quality compression** option:

	wavpack -hh *.dsf

To my surprise, the resulting **.wv** DSD files had a total size of **1.2GB**!


It was time to test these files with [MPD]({{ site.baseurl }}{% post_url 2017-12-22-mpd-and-dsd-files%}). I quickly rebuilt Archphile packages with wavpack support and tested the **highly compressed files** (as this is the most cpu hungry scenario) using the **Archphile/Odroid C2** combo as a transport. In my configuratio, MPD is using only **one and dedicated Odroid C2 CPU core**. The decoding of the .wv file needed approx **25%** of this core.

The most importand part of this test, was to check if the files were recognised as DSD files during playback:

	cat /proc/asound/card*/pcm*p/sub*/hw_params

the output was:

	access: RW_INTERLEAVED
	format: DSD_U32_BE
	subformat: STD
	channels: 2
	rate: 88200 (88200/1)
	period_size: 11025
	buffer_size: 44100
	
	
My trasnport worked as it should in Native DSD mode.

The last test was to see if I can have my dsf files back:

	wvunpack *.wv

I got the **sha256sums** of the extracted dsf files, and I compared with the sha256sums of the initiial dsf files and they were 100% the same. Success!

I am sure that **wavpack compression for DSD files is here to stay**. It's:

- Lossless
- Reversible 
- Very efficient
- Tagging friendly
- Open Source

In other words, It's what flac is to wav files. What remains to be seen is if the communuty will adopt it and make it the DSD standard for computer audio.

