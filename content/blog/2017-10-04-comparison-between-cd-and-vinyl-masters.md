+++
title = "Different CD masters of the same album and a comparison with a vinyl rip - Are there any differences?"
date = "2017-10-04"
thumbnail = "/img/vinyl.jpg"
categories = ["Audio"]
tags = ["cd", "vinyl", "dynamic range"]
+++

Although I am not a big fan of the 70's Rock, there are some albums from this era I love and I always try to find a good CD master  for my digital library.

One of these albums is **Rumours** from **Fleetwood Mac**. Long time ago, I ripped my father's cd with EAC . It's  a US release, for  which unfortunately I don't remember much.  Below  you can  see its dynamic range report  using [DR14 T.meter]({{< ref "2017-09-27-dr14tmeter-a-nice-tool-to-find-the-dr-of-an-album.md" >}}):

	 ---------------------------------------------------------------------------------------------    
	 Analyzed: Rumours /  Artist: Fleetwood Mac
	----------------------------------------------------------------------------------------------   
	DR    Peak    RMS    Duration    Title [codec]    
	----------------------------------------------------------------------------------------------    
	 DR8     -0.10 dB     -10.69 dB    2:56    01 - Second Hand News      [flac]    
	 DR10    -0.10 dB     -11.52 dB    4:16    02 - Dreams      [flac]    
	 DR13    -0.11 dB     -15.78 dB    2:14    03 - Never Going Back Again      [flac]    
	 DR9     -0.13 dB     -11.43 dB    3:12    04 - Don't Stop      [flac]    
	 DR8     -0.10 dB     -9.54 dB     3:43    05 - Go Your Own Way      [flac]    
	 DR12    -0.58 dB     -18.61 dB    3:20    06 - Songbird      [flac]    
	 DR9     -0.10 dB     -13.49 dB    4:29    07 - The Chain      [flac]    
	 DR8     -0.34 dB     -12.54 dB    3:35    08 - You Make Loving Fun      [flac]    
	 DR9     -0.10 dB     -11.53 dB    3:16    09 - I Don't Want To Know      [flac]    
	 DR10    -0.10 dB     -13.82 dB    3:56    10 - Oh Daddy      [flac]    
	 DR8     -0.10 dB     -12.90 dB    4:54    11 - Gold Dust Woman      [flac]    
	----------------------------------------------------------------------------------------------    
	 Number of files:    11
	 Official DR value:  DR9
	    
	 Sampling rate:          44100 Hz
	 Average bitrate:          878kbs 
	 Bits per sample:          16 bit 
	    
	Dr14 T.meter 1.0.16 
	==============================================================================================

and this is a redbook spectrogram of one my favorite songs, **The Chain**:

![The Chain - Bad CD Master](/img/the-chain-bad-cd-master.jpg) 


Although I was not very impressed with the sound quality, I always though that this was an acceptable version I really enjoyed listening to...until I listened to a 24/96 **Vinyl Rip**.

Below you can see the dynamic range of this vinyl rip:


----------------------------------------------------------------------------------------------    
	 Analyzed: Rumours /  Artist: Fleetwood Mac
	----------------------------------------------------------------------------------------------    
	DR    Peak    RMS    Duration    Title [codec]    
	----------------------------------------------------------------------------------------------    
	 DR14     -1.64 dB     -18.99 dB    2:45    01 - Second Hand News      [flac]    
	 DR16     -0.73 dB     -19.64 dB    4:15    02 - Dreams      [flac]    
	 DR15     -6.51 dB     -26.19 dB    2:02    03 - Never Going Back Again      [flac]    
	 DR16     -1.33 dB     -19.48 dB    3:14    04 - Don't Stop      [flac]    
	 DR14     -1.13 dB     -17.64 dB    3:39    05 - Go Your Own Way      [flac]    
	 DR14     -6.48 dB     -27.78 dB    3:20    06 - Songbird      [flac]    
	 DR15     -1.03 dB     -21.63 dB    4:29    07 - The Chain      [flac]    
	 DR14     -1.08 dB     -17.96 dB    3:33    08 - You Make Loving Fun      [flac]    
	 DR16     -1.66 dB     -19.81 dB    3:12    09 - I Don't Want To Know      [flac]    
	 DR15     -1.82 dB     -20.87 dB    3:56    10 - Oh Daddy      [flac]    
	 DR16     -1.02 dB     -21.88 dB    5:15    11 - Gold Dust Woman      [flac]    
	----------------------------------------------------------------------------------------------    
	 Number of files:    11
	 Official DR value:  DR15
	    
	 Sampling rate:          96000 Hz
	 Average bitrate:          2704kbs 
	 Bits per sample:          24 bit
	    
	Dr14 T.meter 1.0.16 
	==============================================================================================


and this is the 24/96 spectrogram of the same song:


![The Chain - VInyl Master](/img/the-chain-vinyl-master.jpg) 


Although a higher dynamic range doesn't mean that the sound is better, I usually find albums with high DR better to my ears. Especially for this album this master is amazing! The sound is more natural, everything is quieter and more balanced and comparing to this, the first cd master was a mess!

I decided to further investigate it and I was very lucky to find and rip a [West German Target](http://www.keithhirsch.com/target-cds) of the same album. Below you can see the DR report of this master:

	----------------------------------------------------------------------------------------------    
	 Analyzed: Rumours /  Artist: Fleetwood Mac
	----------------------------------------------------------------------------------------------    
	DR    Peak    RMS    Duration    Title [codec]    
	----------------------------------------------------------------------------------------------    
	 DR14     -2.96 dB     -20.32 dB    2:46    01 - Second Hand News      [flac]    
	 DR15     -1.69 dB     -20.32 dB    4:16    02 - Dreams      [flac]    
	 DR14     -5.59 dB     -25.03 dB    2:14    03 - Never Going Back Again      [flac]    
	 DR15     -2.16 dB     -20.05 dB    3:12    04 - Don't Stop      [flac]    
	 DR14     -2.35 dB     -18.80 dB    3:39    05 - Go Your Own Way      [flac]    
	 DR15     -9.86 dB     -30.90 dB    3:20    06 - Songbird      [flac]    
	 DR16     -1.80 dB     -23.26 dB    4:29    07 - The Chain      [flac]    
	 DR14     -3.20 dB     -20.72 dB    3:35    08 - You Make Loving Fun      [flac]    
	 DR15     -0.78 dB     -20.16 dB    3:16    09 - I Don't Want To Know      [flac]    
	 DR15     -2.38 dB     -22.49 dB    3:53    10 - Oh Daddy      [flac]    
	 DR15     -5.75 dB     -26.32 dB    4:51    11 - Gold Dust Woman      [flac]    
	----------------------------------------------------------------------------------------------    
	 Number of files:    11
	 Official DR value:  DR15
	    
	 Sampling rate:          44100 Hz
	 Average bitrate:          712kbs 
	 Bits per sample:          16 bit
	    
	Dr14 T.meter 1.0.16 
	==============================================================================================


Quite similar to the vinyl master, right?

Just for the record, this is a spectrogram of the same file:

![The Chain - VInyl Master](/img/the-chain-target-master.jpg) 

This spectrogram is typical for that era, with a low pass filter applied that sets an approx. 20KHz limit.

What about  the sound quality? It's very close to the vinyl rip. Everything is natural and quiet again and this CD release has nothing to do with the first!


Based on all this stuff I would like to share **some final thoughts**:

-  There can't be an actual comparison between vinyl and CD versions of an album. Different mastering procedures will lead to a very different result and it's not fair to blame the CD or the vinyl for this.
- CD masters of old albums are **VERY different**. If a CD version of an album sounds horrible don't blame the format! There might be another that sounds much better!
- Ripping vinyls is a very difficult procedure, but if you know how to do it, the result can be amazing!


 

