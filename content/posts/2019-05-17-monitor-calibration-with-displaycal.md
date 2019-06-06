+++
title = "How I calibrate my monitor with DisplayCAL"
date =  "2019-05-17"
categories = ["Photography"]
tags = ["calibration", "displaycal", "colormunki", "color management"]
+++

In this article I will give you some details on the procedure I follow in order to calibrate my [Dell U2515H](https://www.dell.com/enterprise/p/dell-u2515h-monitor/pd) monitor for optimal photo editing results.

Please note that I am very far from being an expert in this field and that the following information is what I have understood after a whole year of trials and errors.

## My hardware and software configuration

My setup is very complicated comparing to the average photographer's one. My main OS is [Archlinux](https://archlinux.org). For my photographing editing needs I use *Windows 10* on a [KVM virtual machine with GPU Passthrough](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF). This means that although Windows 10 OS runs on a virtual machine, I am able to use a real isolated GPU with that.

So, every time I need to calibrate, I do the procedure twice: one time for **Archlinux/Intel onboard HD 530** and one time for **Windows 10/Nvidia 1050TI**.

## Hardware and software I use for calibration

- [X-Rite Colormunki Display](https://www.xrite.com/service-support/product-support/calibration-solutions/colormunki-display)
- [DisplayCAL](https://displaycal.net/)

Both of them perform fine under Windows and Linux.

## My calibration targets
Although the following values may vary depending on one's needs, they are a safe choice for everyday use:

- **Temperature:** 6500K
- **White level (brightness):** 90cd/m<sup>2</sup>
- **Gamma:** 2.2

Note that many photographers who focus in printing, prefer lower temperatures, ex. **5000K** or **5500K**. I  print my photos too, however I find these settings to be too "yellowish" for everyday use, so I prefer 6500K, which is a safe and widely used value in the digital world.

Regarding the brightness, most of the articles online suggest a value of **120cd/m<sup>2</sup>**. However I find it **extremely bright**, and after a lot of trials and errors I found **90cd/m<sup>2</sup>** to be more than enough for my needs.

## Using DisplayCAL

[DisplayCAL](https://displaycal.net/) is probably the best software for monitor calibration. It offers a really extended and useful [documentation](https://displaycal.net/#toc) that covers almost everything you need to know.

However, a good idea for the average user is to begin with reading the [quick start guide](https://displaycal.net/#quickstart)

Below I will show you my current settings, divided per tab:

### Display & Instrument

![DisplayCAL Display & Instrument tab](/img/displaycal-1.jpg) 

In *Correction*, I chose the suitable correction for [my monitor](https://www.displayspecifications.com/en/model/06291c) based on its specs. You should do a research about yours and apply the appropriate profile.

### Calibration

![DisplayCAL Calibration tab](/img/displaycal-2.jpg) 

I chose **6500K**, **90cd/m<sup>2</sup>** and **Gamma 2.2**. *(See the section below regarding the calibration targets)*, while I set the claibration speed to **Low**.

### Profiling

![DisplayCAL Profiling tab](/img/displaycal-3.jpg) 


I set the profile quality to **High** and chose the **Auto-Optimized** (175 patches) testchart. 

**Note:** I' ve done tests with up to 3400+ patches and I did not see any noticeable difference comparing to Auto-optimized, so I stuck with the latter as calibration takes much less time with it(1 and 1/2 comparing to 4 hours).


### Verification

![DisplayCAL Profiling tab](/img/displaycal-6.jpg) 

Here, I choose the **extended verification testchart** and **sRGB IEC61966-2.1** as this is the standard I want to verify my monitor profile against.

## Procedure

### Calibration

After making sure that all the above settings are correct, I press the button **Calibrate & Profile**. 

The procedure begins and after some initial calculations it's time for the hardware part of calibration.

I press **Start Measurement** and when it finishes, I navigate to **custom color settings** and **brightness** menu of **my DELL U2515H monitor**, and I change various values for brightness and R/G/B values until everything becomes **green** like below:

![DisplayCAL Interactive Display Adjustment](/img/displaycal-4.jpg)

This means that the monitor has come as close as possible to the target settings.

Now, I press **Stop measurement** and **Continue on to calibration**.


After approx 1.5 hour, the profile is ready:

![DisplayCAL Install Profile](/img/displaycal-5.jpg)

### Profile installattion

- On windows I just press **Install profile** and the profile is ready to be used with all the applications that support color management.

- On Archlinux, I navigate to *~/.local/share/DisplayCAL/storage/nameofprofile/* and I copy the **.icc** file. Then I rename it to **profile.icc**, I put it on ~/ICC and load it with:

	xcalib /home/user/ICC/profile.icc		

I use [i3wm](https://i3wm.org/) and I just have to place this command on i3 configuration file so that it is executed every time I log in.

### Verification

For the verification of the newly created profile, I navigate to **Verification tab** (please see the settings above), and I press **Measurement report**.

I choose the location of the html file and after it finishes, the report opens on the default web browser. Below you can see my latest reports for both Archlinux/Intel HD530 and Windows 10/Nvidia 1050ti:

- [Archlinux/Intel HD 530 report](/download/displaycal-reports/displaycal-archlinux-intel-hd530.html)
- [Windows 10/Nvidia 1050ti report](/download/displaycal-reports/displaycal-windows10-nvidia1050ti.html)


## Summary

- The above steps show most of the settings needed for your monitor calibration. If you find any mistake or have any suggestion for improvement, please send me an email.

- Do not get obsessed with monitor calibration. If you take your self seriously as a photographer, it would be a good idea to spend some money for a 99% sRGB (at least) monitor and a colorimeter to calibrate it. The difference will be big, comparing to your old monitor. You will see your images as never before and you will be able to do a much more accurate photo editing. However, always remember that your nicely edited image will be seen by users with non-calibrated monitors, so only you (along with a very small minority of users worldwide) will be able to see the accurate result you worked hard for!

