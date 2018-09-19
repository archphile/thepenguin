+++
title = "How to split a single flac album to separate files (and a funny story about sound quality)"
date =  "2017-10-03"
thumbnail = "/img/cue.jpg"
categories = ["Audio"]
tags = ["linux audio", "cue", "shntool"]
+++

Let's assume that you have a music album in one flac file and you want to split it so that each song is a separate flac file.
The linux tool needed for this task is called [shntool](http://www.etree.org/shnutils/shntool/). In order to install it in Archlinux you need to give the following:

	pacman -S shntool

The command you need to give in order to get the separate files is:

	shntool -f blabla.cue blabla,flac

where blabla.flac is the album **.flac** and blabla.cue its .**cue** file.

One year ago, I wrote about this tool on an audio forum I participate and I realized that there's people that is really concerned about the quality of the output files after the split. It's very easy to assume that I was the only Linux user so I had to find a way to prove that most of the well known splitting tools (including shntool) have the same results. The methodology used was very easy:

**1. I ripped an album twice using EAC: one as a big flac and one with separate flac files.**

**2. I split the files with shntool, and I extracted the flac files to .wav with the following command**:

	flac -d *.flac

**3. I calculated the sha1sums of the .wav files that I got from the split files:**

	sha1sum *.wav > sha1sum_split.txt

The result was:

	051bfcc1866c16a58a888a33bdc3360a96183fa9  split-track01.wav
	0842d6228eee86ec435f9741338e3903c9c84335  split-track02.wav
	a218ff4c8f69c64bbe64665da5dd375932609b7f  split-track03.wav
	03bb5358b14952793329c1ad7a01d2208962f64b  split-track04.wav
	9b7be776d85234e9c7501b3428f8542ee3379fd5  split-track05.wav
	d7e348a556bdd5f7980deea3e767d100f67fd41a  split-track06.wav
	870e02543747f275dfe3e1826367a0699728ff96  split-track07.wav

**4. I used the same commands to extract the flac and calculate the sha1sums using the files of the original rip (the standard one with the separate files).**

The shas1ums were the following:

	051bfcc1866c16a58a888a33bdc3360a96183fa9  01 - track01.wav
	0842d6228eee86ec435f9741338e3903c9c84335  02 - track02.wav
	a218ff4c8f69c64bbe64665da5dd375932609b7f  03 - track03.wav
	03bb5358b14952793329c1ad7a01d2208962f64b  04 - Track04.wav
	9b7be776d85234e9c7501b3428f8542ee3379fd5  05 - track05.wav
	d7e348a556bdd5f7980deea3e767d100f67fd41a  06 - Track06.wav
	870e02543747f275dfe3e1826367a0699728ff96  07 - track07.wav
	
As you can see, there were no surprises. The resulting wav files under both procedures were identical.

Now what about, two very popular windows programs that people use in order to split flacs?

This is the result using [Foobar](http://www.foobar2000.org/): 

	051bfcc1866c16a58a888a33bdc3360a96183fa9  track [1].wav
	0842d6228eee86ec435f9741338e3903c9c84335  track [2].wav
	a218ff4c8f69c64bbe64665da5dd375932609b7f  track [3].wav
	03bb5358b14952793329c1ad7a01d2208962f64b  track [4].wav
	9b7be776d85234e9c7501b3428f8542ee3379fd5  track [5].wav
	d7e348a556bdd5f7980deea3e767d100f67fd41a  track [6].wav
	870e02543747f275dfe3e1826367a0699728ff96  track [7].wav
	
	
and it's obvious that using [CUETools](http://cue.tools/wiki/CUETools_Download) I got the same results.


So, what did I do here? I proved that under all procedures, the resulting wav files were in fact the same files. What is different when using shntool, or foobar or CUETools, is the flac compression level (and please don't start with the affect that flac compression level has in sound in 2017!).

What is very funny, is that even after I presented the above results to this forum, I got replies like *"yes, but I can still hear a difference comparing the split files between foobar and Cuetools"*.. And then I realized how hard is to win an audiophile. Damn, they always win!

