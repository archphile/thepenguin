+++
title = "Fuji cameras, x-trans sensors and RAW processing"
date =  "2018-09-28"
categories = ["Photography"]
tags = ["x-trans", "fuji", "demosaicing", "photography"]
+++


If you are an owner of a **Fuji camera** with an **x-trans** sensor, you will probably have already read a lot about the post processing of x-trans RAF files. Although google is full of results about Fuji RAF files and how the various RAW processors handle them, there are many misconceptions that lead to wrong conclusions. In this post I will try to clarify most of them.

&nbsp;
## The basics

In order to understand **x-trans sensors** and their differences in post-processing, we first need to understand some principles of digital photography:

[Cambridge in Colour - Digital Camera Sensors](https://www.cambridgeincolour.com/tutorials/camera-sensors.htm) 

Assuming that we spent 10 minutes to read this really nice article, it's now obvious to us, that:

- the sensor itself captures information about **the amount of light**

- the filter on top of the sensor captures **information about color**

**Note:** a sensor without this filter can only produce **greyscale** results 


&nbsp;
## The main difference (that affects post-processing) of an x-trans sensor

The most popular filter or to name it even better  **color filter array** for digital cameras is the [Bayer filter](https://en.wikipedia.org/wiki/Bayer_filter) and what makes x-trans sensors different is that **they don't use a Bayer filter.**

![Bayer vs x-trans sensors](/img/bayer-vs-xtrans.jpg) 

Although this is not the only difference between **x-trans sensors** comparing to a typical camera (Bayer) sensor, I won't go into details about the rest (ex. the lack of anti-alising filter), as what I just mentioned is enough to explain the major differences in post-processing.


**Note:**  the image was taken from [Petapixel](https://petapixel.com/2017/03/03/x-trans-vs-bayer-sensors-fantastic-claims-test/).


&nbsp;
## Demosaicing - from RAW data to an image

What is very important to understand, is that **a RAW file is not an image**. It is just a file with data and it needs a lot of mathematical processing before it starts looking like one. The first major step of converting these data to an image, is **demosaicing**:

{{< youtube 9cPxEFpg3Eg>}}

Each pixel has:

- information about the amount of light (from the sensor)
- information about **one color**, R or G or B **only**

Using mathematical calculations (demosaicing) we try to guess the remaining two colors of each pixel.

&nbsp;
## Differences between RAW editors on x-trans files

When we import a RAW file on a RAW editor like Lightroom or Capture One, the image that we see, is a preview of our **demosaiced RAW data** along with **additional sharpening**, **noise reduction** etc..

As most of the cameras use a Bayer filter, all companies and communities have spent money and time on creating demosaicing algorithms based on the **Bayer filter**.

**X-trans filter uses a different color pattern** and so the traditional demosaicing algorithms **cannot be applied** on RAF files from  x-trans based cameras. 

This is the reason that all companies (and communities) that support this kind of files, **had to write additional code** to handle the data from x-trans color filter array! 

So by now, it should be clear that when we open a NEF file and an x-trans RAF one in Lightroom for example, the latter uses a different algorithm to handle the NEF comparing to the RAF. 

This is the exact reason that Lightroom is ok for most of the RAW files of various companies, but "it sucks" with x-trans RAF!

By now, **it should be obvious how important demosaicing is**, but for the final post-processing **we should consider many additional parameters**.

&nbsp;
## The X editor is better than the Y!!

Ok, we might be correct, but we need to keep in mind that these two programs:

1.  **handle demosaicing differently** and this can't be changed
2.  **handle dynamic range recovery differently** and this can't be changed
3. **handle sharpening and noise reduction differently** - this can't be changed, but we can do a lot to bring them close enough
4. **handle color differently** but we can make the results identical
5. **handle contrast differently** but we can make the results identical

Us, being Fuji x-trans camera owners, **we care a lot about 1!!**

If we opened an x-trans file in both Lightroom and Capture One and we found the colors and contrast of the latter better for example,  it's not that Lightroom's colors and contrast suck! It's just that we prefer the preset colors and contrast of Capture One. If we have the knowledge, **we can have the exact same result everywhere**.  

&nbsp;
## Well known RAW editors and how they handle x-trans RAW files

### Lightroom

Lightroom is one of the most well known RAW editors. Although it does a great job with most of the RAW files, it can't handle x-trans RAW data very well. 
Usually to see most of what Lightroom doesn't do very well with  x-trans files, we have to do some pixel peeping. However, it's true that it has issues with **foliage** and **(over-)sharpening** and in general it **lacks detail** when compared with other RAW editors.

**Note:** Lightroom does not have issues with sharpening, but with **oversharpening**. This means that in order to see the famous "worm" artifacts, we need to push sharpening settings a lot.

### Capture One

Capture One does a great job with x-xtrans RAF files. This is the software I am currently using.

### RawTherapee and Darktable

These two amazing open source programs have very advanced demosaicing algorithms to handle x-trans files. I haven't done many tests with Darktable, but testing  RawTherapee, I was amazed with the results, especially when comparing with what Lightroom can do.

### Iridient X-transformer 

Iridient X-transformer became famous as a **RAF to DNG converter** for people that use Lightroom (ising the DNG).
IXT has many different options (mainly affecting **sharpening** and **noise reduction**) that bring different results. It's famous for handling details nicely, but IMHO it has some troubles with noise in high ISOs.

DNG files from IXT **ARE NOT RAW files** as **they have been already demosaiced** . This means that when we open a DNG from IXT in Lightroom or Capture One, **we don't use** their demosaicing algorithm!!! It's more like opening a tiff file.

For example, when we compare a RAF opened with Capture one with a DNG from IXT opened in Lightroom, and we do pixel peeing to compare details, foliage, etc, in fact we compare C1 with IXT!

To sum up, Iridient X-transformer should be considered a RAW "editor" and not just a converter as i**t applies demosaicing, sharpening and noise reduction** and **the DNG it outputs is not RAW** (DNG files can be RAW, but these specific ones aren't!).

&nbsp;
## Summary

- **Demosaicing** is really important. When an editor sucks with an x-trans RAF file, the usual suspect is the demosaicing algorithm.

- Even though there are differences between RAW editors and their results with x-trans files, most of the differences **need pixel peeping** to be seen.

- **Pixel peeping is bad for photography**. Ask your doctor today on how to get rid of this health destroying **obsession**!
 


