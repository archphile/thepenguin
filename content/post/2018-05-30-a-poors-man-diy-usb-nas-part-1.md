+++
title = "A poor man's DIY USB NAS part I"
date = "2018-05-30"
thumbnail = "/img/samba.jpg"
categories = ["General"]
tags = ["nas", "usb disk", "samba", "archlinuxarm"]
+++

Back in 2014, when I started developing [Archphile](http://archphile.org), I was using my desktop PC with [samba](https://www.samba.org/)  in order to share my music to my transport. After almost a year I decided that I didn't want my PC to be running every time I needed to listen to some music. Besides this, my PC was and still is in a small room, very close to my hi-fi, so being heavily obsessed with fan noises (and usually listening to music at low levels), I decided that it was time to create my first "quick and dirty" **USB NAS**.

I was already using a **Devolo** powerline solution to connect to a Raspberry Pi/Openelec at the living room, so this NAS would go to the other side of the house (close to the RPI) so that I could not hear even the fan noise of the USB disk.

To cut the long story short, for my first implementation I used:

- a **cubox-i4** pro with [ArchlinuxARM](https://archlinuxarm.org) 
- a WD usb disk **Mybook 2T**

I started looking for various software solutions in order to implement a complete NAS solution and after a lot of research I ended up with an installation that included:

- Samba
- NFS
- Minidlna server
- Transmission torrent client
- USB disk automounting with udevil
- USB disk spinning down with hd-idle/hdparm

etc..

I started using it immediately as a combo with [Archphile](http://archphile.org), as my only need at that time was just to serve my music.

That was when I thought that it would be nice if I sat down and make a Raspberry Pi image (cubox-i was expensive and difficult to find) with all this stuff and share it with the members of a Greek forum I used to be a very active member back then. 

....And this is why I created one of the most unsuccessful projects on planet earth: [Phileserve](https://github.com/archphile/phileserve)! 

**Phileseve** was an image for the Raspberry Pi that included everything. It even had a [manual](https://github.com/archphile/phileserve/blob/master/phileserve-0.1-guide.pdf) (which I used as a base many years later to write the [Archphile manual](http://archphile.org/archphile-manual/) ).

Considering the really low cost of this implementation, its performance was quite acceptable. Below you will find some tests I did with the Raspberry Pi:

**Write**

	dd if=/dev/zero of=/mnt/test/testfile bs=1M count=1024 oflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB) copied, 115.133 s, 9.3 MB/s

**Read**

	dd if=/mnt/test/testfile of=/dev/null bs=1M count=1024 iflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB) copied, 106.425 s, 10.1 MB/s


Not bad at all, especially for a NAS just serving the "music library".


Anyway, I shared my work on that forum, almost no one cared about it, so I stopped wasting my time  and just kept using **Phileserve** for my own needs.

After more than two years of use with the cubox-i4, I replaced the board with an Odroid C1+ and that combo served me until the summer of 2017, when I decided that it was not enough for me..

**Note 1:** Phileserve Github repository is still up (and very outdated) and from time to time I push some configuration changes for files like the smb.conf mainly in order to backup. You never know..

**Note 2:**  Using a NAS along with a powerline is not a very clever idea. During all these years this NAS had noticeable speed performance fluctuations and based on all the tests I did, the usual suspect was always the powerline solution.