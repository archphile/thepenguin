+++
title = "Fuji X-T20 film simulation packs for Darktable and RawTherapee"
date = "2018-01-21"
thumbnail = "/img/fuji-provia.jpg"
categories = ["Photography"]
tags = ["Fuji", "x-t20", "film", "darktable", "rawtherapee"]
+++

In my previous [post about photography] ({{< ref "2018-01-16-fuji-xt20-film-simulation-pack-for-capture-one.md" >}}), I showed you how to get **Fuji X-T20** film simulations for **Capture One**. In this one I will show you the same but for [Darktable ](https://www.darktable.org/) and [RawTherapee](http://rawtherapee.com/). Please note that all these styles are not only compliant with **X-T20** but they can be used with all **X-TRANS III** cameras.

### RawTherapee
Thanks to the amazing job by [Stuart Sowerby](https://blog.sowerby.me), our community has now available all currrent Fuji film simulations *(Provia, Velvia, Astia, Classic Chrome, Pro Neg Hi, Pro Neg Std, Acros, Acros + Ye, Acros + R, Acros + G, Mono, Mono + Ye, Mono + R, Mono + G and Sepia)*. If you visit [this link](https://blog.sowerby.me/fuji-film-simulation-profiles/) , you will find various different simulation packages suitable for different Raw editors. For **RawTherapee**, you need to donwload the following package:

- [Fujifilm-XTrans-III.zip](https://blog.sowerby.me/wp-content/uploads/2018/01/Fujifilm-XTrans-III.zip) 

- [Fujifilm-XTrans-III.zip](/download/Fujifilm-XTrans-III.zip) (Alternative Download Link hosted on my website)*

 Then you need to follow the instructions for [HaldCLUT](http://rawpedia.rawtherapee.com/Film_Simulation) .
 
 What I did in Archlinux was to extraxt the zip, then create a HaldCLUT directory under **~/.config/RawTherapee** and  set the HaldCLUT location in RawTherapee **Preferences**.

### Darktable
Thanks to [Andy Constanza](http://andycostanza.com/) and [Jean Paul Gauche](https://www.facebook.com/jeanpaul.gauche) , the styles above where converted for [Darktable](https://www.darktable.org/) You can get the styles below, extract the zip and import them using the styles module in lighttable tab :

 - [Fuji_XTrans_III_dtstyles.zip](https://darktable.fr/download/Fuji_XTrans_III_dtstyles.zip)
 
 - [Fuji_XTrans_III_dtstyles.zip](/download/Fuji_XTrans_III_dtstyles.zip) *(Alternative Download Link hosted on my website)*


As per [Stuart's Sowerby](https://blog.sowerby.me) usage notes:

>The simulations are designed to be applied to a neutral RAW file, this means no auto-levels or custom tone curves / contrast should be applied, although you can still use the exposure slider to correct initial brightness. Any processing to the image should ideally happen AFTER you’ve applied the simulation or you may get unintended results.