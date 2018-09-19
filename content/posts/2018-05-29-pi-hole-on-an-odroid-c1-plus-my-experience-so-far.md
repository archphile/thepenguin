+++
title = "Using Pi-hole on an Odroid C1+ - My experience so far"
date = "2018-05-29"
thumbnail = "/img/pihole.jpg"
categories = ["General"]
tags = ["pi-hole", "odroid c1+","adblock"]
+++

After dropping **Odoid C1+** support in [Archphile](http://archphile.org), I had this board available and ready for a new project.

For more than a year, I used [privoxy](https://www.privoxy.org/) on a ["Netgear R7000"](https://www.netgear.com/home/products/networking/wifi-routers/R7000.aspx) router with [DD-WRT](https://dd-wrt.com/) as my main ad-blocker, but I wanted something easier and more configurable for a daily driver.

This is why I decided to install [pi-hole](https://pi-hole.net/) pi-hole on the Odroid C1+.

![Pi-hole Overview](/img/pihole-odroidc1.jpg  "Pi-hole")

**Pi-hole** was initialy created for **Raspbian/Raspberry Pi**, but it can run on any **Debian/Ubuntu/Centos** box. So I downloaded [Armbian Ubuntu xenial](https://dl.armbian.com/odroidc1/Ubuntu_xenial_default.7z) , wrote it on an sd card and booted it.

Using the following command:

	armbian-config

I was able to configure the basic [Armbian](https://www.armbian.com/)  stuff (static IP, hostname, timezone etc..)

Then I fully updated the system (you can do it via armbian-config too - I prefer the "classic" way):

	apt-get update && apt-get upgrade

and continued to the installation of pi-hole:

	wget -O basic-install.sh https://install.pi-hole.net
	bash basic-install.sh

After Pihole installation, I downloaded and modified my adlists.list file, enabling most of the extra sources:

	wget https://raw.githubusercontent.com/archphile/pihole_stuff/master/adlists.list -O /etc/pihole/adlists.list
	pihole -g

and a package cache cleanup:

	apt-get clean

Finally I tweaked some Odroid related stuff:

	wget https://raw.githubusercontent.com/archphile/pihole_stuff/master/rc.local-odroid-c1 -O /etc/rc.local

	wget https://raw.githubusercontent.com/archphile/pihole_stuff/master/log2ram -O /etc/default/log2ram

Once a week, I check for updates in ad lists with:

	pihole -g	

When I get notifications on the web interface that a new version is available, I update with the following command:

	pihole -up

### Summary and Notes

[Pi-hole](https://pi-hole.net/) is an amazing piece of software. It's highly configurable, extremely easy to install and **it does the job right**, as It blocks the majority of ads that can be blocked via **DNS**. 

If you have an available Raspberry Pi or any other board that can get Debian/Ubuntu on it and you care about privacy/adblocking, Pi-hole is a must.

