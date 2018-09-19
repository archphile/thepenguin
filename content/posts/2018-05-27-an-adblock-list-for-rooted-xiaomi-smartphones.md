+++
title = "An adblock list for rooted Xiaomi smartphones (and more)"
date = "2018-05-27"
thumbnail = "/img/adaway.jpg"
categories = ["General"]
tags = ["xiaomi", "pi-hole", "adblock", "adaway"]
+++

3 months ago I decided to [install and use pi-hole on my Odroid C1+](https://github.com/archphile/pihole_stuff). Using **rooted** Xiaomi smartphones for years now (my latest is a **Mi Max2** tablet), I decided to keep an eye on xiaomi urls that [pi-hole](https://pi-hole.net/)  blocked from my device and create a hosts file for [Adaway](https://adaway.org/)  so I have the same rules enabled when not using wifi at home. Who wants device manufacturers to spy anyway?

This is how and why the following list was created:

[http://thepenguin.eu/download/tp-adblock.txt](http://thepenguin.eu/download/tp-adblock.txt) 

Although my initial thought was to keep this list focused on xiaomi urls (I have also included plenty of xiaomi urls found online), I expanded it so that it includes various adiitonal urls that my phone kept communicating with.

The list above can be used both an **Adaway** and **pi-hile** host source.

Feel free to fork the following repo:

[https://github.com/archphile/pihole_stuff](https://github.com/archphile/pihole_stuff) 

modify the **tp-adblock.txt** file and send me your suggestions back so that I include  them on the list! 
