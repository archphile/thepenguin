+++
title = "A (not so) poor man's DIY USB NAS part II (DD-WRT edition)"
date = "2018-05-31"
thumbnail = "/img/ddwrt.jpg"
categories = ["General"]
tags = ["nas", "usb disk", "samba", "ddwrt", "Netgear R7000"]
+++

As mentioned in my [previous post]({{ site.baseurl }}{% post_url 2018-05-30-a-poors-man-diy-usb-nas-part-1%}), during the summer of 2017 I decided that it was time to replace my first diy USB NAS. 

I had already bought a **Netgear R7000**  to use it with [DD-WRT](https://dd-wrt.com/) that supported USB 3 disk sharing via [samba](https://www.samba.org/), I had a lot of embedded boards running at home for various tasks and I wanted to get rid some of them and the most important, I needed more space as I wanted to use the NAS for other tasks apart from serving my music files.

So I bought a **Western Digital Red 3T** and I put it in a  USB 3 passive aluminium case (unfortunately, I don't remember the brand, but it didn't cost more than 40 euro). The new NAS would be at the same smallo room along with the hi-fi, so I wanted to avoid any new fan..

 I formatted it using **ext4** filesystem and plugged it on the USB 3 (that actually runs at a much lower speed) port of the **R7000**.

 The [DD-WRT](https://dd-wrt.com/) configuration was pretty easy and straight forward. 
 
 ![DD-WRT overview](/img/ddwrt-samba.jpg  "DD-WRT")
 
 I created 9 samba shares to better organize music, images, PC backup stuff etc.., I created samba users, set passwords and my new NAS was ready to use!
 
 The first I wanted to see was how it performed:
 
 
**Read**

	dd if=/mnt/ddwrt/music/testfile of=/dev/null bs=1M count=1024 iflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB, 1.0 GiB) copied, 30.0215 s, 35.8 MB/s


**Write**

	dd if=/dev/zero of=/mnt/ddwrt/music/testfile bs=1M count=1024 oflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB, 1.0 GiB) copied, 27.7596 s, 38.7 MB/s



Ok, for a Gigabit network active equipment and a USB 3 disk, I admit I expected more, but **I got almost 4 times the performance of my old NAS**. Not bad at all! 

The only drawback comparing to my old implementation is that the [kong DD-WRT build](http://www.desipro.de/ddwrt/K3-AC-Arm/Supported%20Models) I am using doesn't have the **hd-idle** tool pre-installed  (I need to find the time and fix this) in order to spin down the disk when not in use (in theory WD Reds don't need that), but:



- this NAS (and the previous one) is not running 24/7/365. I don't need this to be always on so every night is powered off

- I keep a double (to be more specific a [semi triple]({{ site.baseurl }}{% post_url 2018-06-01-how-i-backup-everything-using-rsync%})) backup of most of my data, so I won't cry if the disk dies

and so I don't get crazy for not using hd-idle until today.

### Summary

I am really satisfied with this new USB NAS. It does the job well and using it for months now, I never had any issues with that. 

I always believed that not everyone needs a "real",  NAS. If you don't have any "special" needs, and especially If you are looking for a NAS to serve your music, you should really consider a solution like that. 

If you can afford the money to buy a decent router that can be flashed with **DD-WRT**, I highly recommend you to do so. Apart from the NAS, you will get increased and stable network performance, advanced wireless configuration options, QoS, privoxy proxy/adblocker, dnsmasq server (that offers DNS caching), minidlna, ftp, but we will discuss about them on another post!