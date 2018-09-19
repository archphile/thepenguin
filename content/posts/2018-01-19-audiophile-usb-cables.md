+++
title = "Audiophile USB Cables and snakeoil"
date = "2018-01-19"
thumbnail = "/img/snakeoil-square.jpg"
categories = ["Audio"]
tags = ["usb", "snakeoil"]
+++

Reading a forum thread regarding "audiophile" **USB cables** for computer audio, I rememembered a really nice [head-fi.org](https://www.head-fi.org/threads/on-usb-cables-and-controller-transfer-modes-a-series-of-questions-to-replies-from-usb-org.565791/) topic, where a forum member named **svyr** decided to send some questions about **usb and audio** to [usb.org](http://www.usb.org).

![snakeoil](/img/snakeoil.jpg  "snakeoil")

To his surprise, he got a reply and below I will quote the whole email conversation **without any further comment** from my side:

### Email to usb.org

	From: svyr [mailto:xf_mad:gmail.com]
	Sent: Wednesday, August 03, 2011 4:27 AM
	To: admin [AT] usb.org
	Subject: usb audio (class 1 and 2) and cable affecting sound?
	
	Hello,
	
	Major debates are raging about Class 1 or 2 USB audio devices (TE7022,
	TAS1020B, etc receiver chips),
	operating in adaptive or asynchronous isochronous modes being or not
	being affected by
	by 'quality' of the USB cable used.
	(http://www.head-fi.org/forum/thread/554008/don-t-get-why-audiophile-usb-cable-would-improve-sound-quality/645#post_7651352)
	
	
	I'm not going to bore you with much detail, but people seem to think
	'audiophile' cables,
	somehow improve sound quality by "reducing transmission errors and
	'jitter'" over to spec/certified
	USB cables.They also seem to think custom cables improve sound by
	using better shielding/allegedly higher conductivity wires.
	
	Personally I think it's all expensive placebo and waffle and because
	of the cost/margin on some of those
	cables
	http://www.wickeddigital.com.au/index.php?page=shop.product_details&flypage=joomlaplates.tpl&product_id=801&category_id
	=80&option=com_virtuemart&Itemid=53
	fraud.
	
	I was wondering if usb.org could comment on the issue, including any
	influence they think
	an after-market USB cable can have theoretically, and perhaps empirically.
	
	Best Regards,
	[svyr]

### Reply

	[quote name="TechAdmin [AT] usb.org"]
	to svyr
	date Fri, Aug 5, 2011 at 5:46 AM
	subject RE: usb audio (class 1 and 2) and cable affecting sound?
	
	Hello [svyr],
	
	USB transmits information digitally. Bits are either received correctly or
	not received. What a bit looks like on the wire has no effect on quality if
	the bit is received correctly. If a bit is not receive correctly, error
	checking in USB protocols will flag the error in data transmission.
	
	Jitter is not a cable problem. Jitter is a transceiver (PHY) issue on the
	devices.
	
	Can bits get scrambled within a cable assembly on occasion? Yes, primarily
	due to EMI but this is highly unlikely -- more on that later. Is occasional
	data scrambling a problem for audio/video? Maybe. The answer depends on the
	hardware receiving/rendering the data.
	
	USB supports isochronous transport which is a timely delivery of data. The
	isochronous transport has guaranteed bandwidth on USB. Isochronous
	protocol, however, does not support error recovery. In other words, if data
	is flagged as an error by the receiver, there will be no attempt at data
	retransmission. So if the receiver is using the isochronous protocol, then
	there can be errors in data. Most webcams use the isochronous transport.
	High-end audio/video equipment that does not mandate real-time delivery of
	data should not use the isochronous transport because accurate data delivery
	is not guaranteed.
	
	USB also supports bulk transport. The Bulk transport shares bandwidth and
	timely delivery is not guaranteed. Bulk protocol does have error recovery
	and errors in data will be retried. If the receiver uses the bulk USB
	protocol, then there will be no errors in the data. This is why USB mass
	storage devices always use the Bulk transport.
	
	Most USB audio/video devices use the bulk transport because real-time
	delivery of the data is not necessary. Bulk audio/video devices will buffer
	data before rendering it. I can think of only two situations where the
	audio/video will be disturbed when rendered: 1) If the host is busy
	performing IO to other USB devices, or 2) There are errors in data
	transmission where continual retries cause buffer under-run to occur. The
	second point could be cable related -- it could also be poor hardware design
	of the host or peripheral as well. The USB Bulk transport works very nicely
	for audio and video because data is accurately delivered. 
	
	Now onto cable quality. A cheap USB cable will work perfectly fine in the
	vast majority of home/office environments. All USB certified cables use
	certified connectors and are shielded, have minimal skew on the data lines,
	and meet criteria regarding impedance and voltage drop. If the environment
	is extremely noisy with EMI, then a better shielded cable may be necessary.
	Usually relocating the cable or power strips will suffice to mitigate EMI.
	
	Personally, I would never recommend anyone buy an expensive USB cable unless
	they are experiencing problems not related to their hardware and there
	exists definitive suspicions of environmental interference. I do always
	recommend that the cable purchased be USB certified which provides assurance
	that the product is properly designed for USB. Using USB certified
	audio/video equipment also assures that the USB signal quality and other
	packet parameters of the transceiver meets specifications.
	
	Of course, all of the above is premised upon properly designed and
	functioning hardware.
	
	Regards,
	Mark Paxson
	USB-IF Compliance Administrator
	TechAdmin@usb.org
	(ReplyID 110804.105337)



