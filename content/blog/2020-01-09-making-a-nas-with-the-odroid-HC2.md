+++
title = "Making a NAS with the Odroid HC2"
date =  "2020-01-09"
categories = ["General"]
tags = ["NAS", "Odroid HC2", "Openmediavault"]
+++

Last a year I decided to upgrade my DIY USB NAS (you can read my journey so far [here]({{< ref "2018-05-30-a-poors-man-diy-usb-nas-part-1.md" >}}) and [here]({{< ref "2018-05-31-a-poors-man-diy-usb-nas-part-2.md" >}})) and for this reason I bought an [Odroid HC2](https://www.hardkernel.com/shop/odroid-hc2-home-cloud-two/).

This would be a big upgrade for me, as for the first time I would be able to connect my **WD Red 3T** via SATA and not via USB.

So, I bought one and let's see below how it went...

![My HC2](/img/hc2.jpg)

## The hardware

Odroid C2 is a nice tiny board, made specifically in order to serve as a NAS.

Some of its key features are:

* Samsung Exynos5422 Cortex-A15 2Ghz and Cortex-A7 Octa core CPUs
* 2Gbyte LPDDR3 RAM PoP stacked
* SATA-3 port for 3.5inch or 2.5inch HDD/SSD  storage up to 27mm thickness
* Gigabit Ethernet port
* USB 2.0 Host
* UHS-1 capable micro-SD card slot for boot media
* Size : 197 x 115 x 42 mm approx.(Aluminium cooling frame size)
* Linux server OS images based on modern Kernel 4.14 LTS

When I received it, I plugged in my WD Red on the **SATA-3** port and then I started examining which OS I would use for my NAS.

## The software

If you are a reader of this blog, you will have already understood that apart from being a geek, I am a control freak too. I need to know what exactly is going on with regards to the OS, processes etc..

Normally, I would install [ArchlinuxARM](https://archlinuxarm.org/), samba, etc, to create a 100% tailored OS for my needs. This time I decided to choose a different route and it proved to be the right choice..

### Openmediavault

So I downloaded the [OMV](https://www.openmediavault.org/) image for HC2, wrote it on the SD card and booted for the first time.

Openmediavault, is the exact opposite when compared to my 100% custom CLI based installations. It has a really nice web interface where you can easily configure your NAS in minutes and it has [a LOT of features](https://www.openmediavault.org/features.html) that will cover most of the average (and advanced..) user's needs:

![OMV screenshot](/img/omv1.png) 


My first task was to upgrade the OS. In [this forum post](https://forum.openmediavault.org/index.php/Thread/19618-OMV-3-for-ODROID-XU4-HC1-HC2-MC1/?postID=199781#post199781) you can read about some issues I had when trying to do so plus how I solved them.

Next, I created the needed samba shares and started testing the new NAS.

## Performance

Performance wise, the HC2/Openmediavault combo proved to be more than enough for my needs:

**Read**

	dd if=/mnt/nas/music/testfile of=/dev/null bs=1M count=1024 iflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB, 1.0 GiB) copied, 10.0303 s, 107 MB/s

**Write**

	dd if=/dev/zero of=/mnt/nas/music/testfile bs=1M count=1024 oflag=direct
	1024+0 records in
	1024+0 records out
	1073741824 bytes (1.1 GB, 1.0 GiB) copied, 10.9383 s, 98.2 MB/s


## The HC2 as a Pi-hole box in parallel with OMV

In [this post]({{< ref "2018-05-29-pi-hole-on-an-odroid-c1-plus-my-experience-so-far.md" >}}) I explained how I used the Odroid C1+ in order to create a pihole box. 

After finishing with the configuration of the NAS, I decided to make HC2 a Pi-hole box too so that I could get rid of the C1+.

In order to access the web interface I had to modify the web port of Lighttpd to 8080. The URL for the pi-hole admin interface became:

	xxx.xxx.xxx.xxx:8080/admin


## Summary

- The HC2 is a huge upgrade when compared to my previous USB DIY NAS.

- Openmediavault is a really nice piece of software. 

- If you are on a tight budget and you don't care about RAID, the Odroid HC2/Openmediavault combo is a highly suggested solution!