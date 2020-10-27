+++
title = "myMPD - my new favorite MPD client"
date = "2018-06-04"
thumbnail = "/img/mympd.jpg"
categories = ["Audio"]
tags = ["linux audio", "MPD", "myMPD", "ympd"]
+++

I hate bloated software. This is the reason I use [Archlinux](https://archlinux.org)  with [i3wm](https://i3wm.org/) or I root my smartphones to remove unneeded applications and this is the exact same reason I chose [ympd](https://github.com/notandy/ympd) to be the default [MPD](https://www.musicpd.org) client of [Archphile](http://archphile.org).

**ympd** doesn't offer many goodies. It does one thing (file browsing mode) and it does it right, while its software dependencies are almost zero, comparing to other web based clients that need a dedicated web server or/and interpreter..

**ympd** drew the attention of various coders that forked this project, [bugfixed it](https://github.com/SuperBFG7/ympd)  or created new projects based on that.

This is exactly how my new favorite client, [myMPD](https://github.com/jcorporation/myMPD) ,was created being a fork of a [ympd fork](https://github.com/SuperBFG7)!

[myMPD](https://github.com/jcorporation/myMPD), is a huge improvement over ympd. [Jcorporation](https://github.com/jcorporation)  (myMPD coder), with the addition of open source tools like **bootstrap 4**, managed to offer a ton of useful new features, without transforming the client to a bloated and heavy software. 

The resources [myMPD](https://github.com/jcorporation/myMPD) needs on an **Odroid C2** or a **Raspberry Pi** are (like with ympd) really low, while Archlinux package dependencies remain the same with **ympd**.

But let's stop with words and see some action:


**- Browsing in Filesystem mode:**

![Browse Filesystem section](/img/mympd-1.jpg  "myMPD")

![Album directory view](/img/mympd-2.jpg  "myMPD")


**- Browsing in Database mode:**

![Browse in Dartabase section](/img/mympd-5.jpg  "myMPD")


**The Search tab:**

![myMPD search tab](/img/mympd-8.jpg  "myMPD")


**- Album added in Queue:**

![myMPD Queue](/img/mympd-3.jpg  "myMPD")


**- Playback tab showing local cover art:**

![myMPD Playback tab](/img/mympd-4.jpg  "myMPD")


**- myMPD Menu and Settings:**

![myMPD menu](/img/mympd-6.jpg  "myMPD")


![myMPD settings](/img/mympd-7.jpg  "myMPD")


## What I really like:

1. The support of local cover art and the fact that each user can choose the cover file name they use (ex. I modified myMPD settings to always show **Folder.jpg** found on each of my library albums)

2. The new search functions: It's really nice to be able to search by tag. Especially when searching by album, the user can load a whole album with the use of one button!

3. The database view: I really like to have the option to navigate by Artist, see their albums and load music to queue this way!

4. The new look: The new layout is fantastic, although the colors aren't my favorites (who cares anyway!).


## What I don't like:

1. I didn't like all these extra crossfading, replaygain and mixramp options. I completely understand that there's people using them, so they have to be there (although I am not sure how many people even knew that they could use mixramp!).

2. The states of the tabs are currently not saved. I am sure that Jcorporation will do his magic very soon and fix that.

## Summary:

[myMPD](https://github.com/jcorporation/myMPD) is a **fantastic** new piece of software.  As long as development continues with **simplicity in mind**  (and of course low resource usage!), I'm sure that **myMPD** will set new standards on MPD clients.
 
 
**Note 1:** It's obvious that next **Archphile** will include the option to use [myMPD](https://github.com/jcorporation/myMPD) (and why not make it the default one if it is stable enough for everyday use)

**Note 2:** I will prepare and upload [myMPD](https://github.com/jcorporation/myMPD) packages to be used with **0.99.73**. I will post all required information on [Archphile website](http://archphile.org) when everything is ready.

**Note 3:** [myMPD](https://github.com/jcorporation/myMPD) is a really new software. If you test it and something is not working the way it should (or you want), don't blame the project! Give it some time and, the most important, [feedback](https://github.com/jcorporation/myMPD/issues)!

**PS.** *The credit for finding this nice software goes to my good friend Emilios, who, for the last 5 months,  has been heavily obsessed with testing almost all ympd forks!*
