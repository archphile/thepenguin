+++
title = "How to verify CD rips with AccurateRip database"
date =  "2017-09-28"
thumbnail = "/img/accuraterip.jpg"
categories = ["Audio"]
tags = ["linux audio", "accuraterip"]
+++

When we need to verify the quality of a CD rip, one of the most powerfull tools we have is the [AccurateRip database](http://www.accuraterip.com/).

Although I won't go into details on how I rip my CDs (yes, I use EAC with wine :P), I will show you two easy procedures on how to verify a  CD rip using AR database.


### First Method (Linux Native)

All we need for the first method is [whipper](https://github.com/JoeLametta/whipper). In order to install it in Archlinux, we need the following command:

	pacman -S whipper

After the installation is complete, we just need to navigate to a flac album and use the following command with the non-compliant .CUE we have created during the ripping procedure:

	whipper image verify blabla.cue	

This is a typical output of the above command when everything is fine:

	Track  1: rip accurate     (confidence   3 of   4) [4523177f], DB [4523177f]
	Track  2: rip accurate     (confidence   3 of   4) [23c641fd], DB [23c641fd]
	Track  3: rip accurate     (confidence   3 of   4) [84fda1ca], DB [84fda1ca]
	Track  4: rip accurate     (confidence   3 of   4) [59ea0b32], DB [59ea0b32]
	Track  5: rip accurate     (confidence   3 of   4) [ba26bc6f], DB [ba26bc6f]
	Track  6: rip accurate     (confidence   3 of   4) [450aeeca], DB [450aeeca]
	Track  7: rip accurate     (confidence   3 of   4) [eef9d6ed], DB [eef9d6ed]
	Track  8: rip accurate     (confidence   3 of   4) [75bc1fa8], DB [75bc1fa8]
	Track  9: rip accurate     (confidence   3 of   4) [c3830abc], DB [c3830abc]
	Track 10: rip accurate     (confidence   3 of   4) [3c6c1d96], DB [3c6c1d96]
	Track 11: rip accurate     (confidence   3 of   4) [559661ae], DB [559661ae]
	Track 12: rip accurate     (confidence   3 of   4) [99ad4537], DB [99ad4537]
	Track 13: rip accurate     (confidence   3 of   4) [925c2458], DB [925c2458]
	Track 14: rip accurate     (confidence   3 of   4) [5ae4616d], DB [5ae4616d]
	Track 15: rip accurate     (confidence   3 of   4) [5c50b853], DB [5c50b853]
	Track 16: rip accurate     (confidence   3 of   4) [c6e438f2], DB [c6e438f2]
	Track 17: rip accurate     (confidence   3 of   4) [04abe75c], DB [04abe75c]
	Track 18: rip accurate     (confidence   3 of   4) [22242ab9], DB [22242ab9]
	Track 19: rip accurate     (confidence   3 of   4) [faaaf059], DB [faaaf059]
	Track 20: rip accurate     (confidence   3 of   4) [6087c48e], DB [6087c48e]
	
&nbsp;
### Second Method (Using WIne)

For this method (which is the one I prefer), we first need to install wine. Again for Archlinux the command is:

	pacman -S wine

Now we need to download the latest available version of [CUETools](http://cue.tools/wiki/CUETools_Download) and extract it on our home folder. A good idea is to rename the directory to something easy, ex. **cuetools**.

Now the command we need to use in order to verify the image is:

	wine /home/your_username/cuetools/ArCueDotNet.exe blabla.cue

A typical output for this command is the following:

	[CUETools log; Date: 9/28/2017 11:43:27 AM; Version: 2.1.5]
	[CTDB TOCID: SVOZo65GWrYcVLA6G_eJxMqAF4Q-] found.
	Track | CTDB Status
	  1   | (12/13) Accurately ripped
	  2   | (12/13) Accurately ripped
	  3   | (12/13) Accurately ripped
	  4   | (12/13) Accurately ripped
	  5   | (12/13) Accurately ripped
	  6   | (12/13) Accurately ripped
	  7   | (12/13) Accurately ripped
	  8   | (12/13) Accurately ripped
	  9   | (12/13) Accurately ripped
	 10   | (12/13) Accurately ripped
	 11   | (12/13) Accurately ripped
	 12   | (12/13) Accurately ripped
	 13   | (12/13) Accurately ripped
	 14   | (12/13) Accurately ripped
	 15   | (12/13) Accurately ripped
	 16   | (12/13) Accurately ripped
	 17   | (12/13) Accurately ripped
	 18   | (12/13) Accurately ripped
	 19   | (12/13) Accurately ripped
	 20   | (12/13) Accurately ripped
	[AccurateRip ID: 003a1714-034b497e-4611e714] found.
	Track   [  CRC   |   V2   ] Status
	 01     [4523177f|f57bc8ad] (3+2/9) Accurately ripped
	 02     [23c641fd|18790680] (3+2/9) Accurately ripped
	 03     [84fda1ca|5aa0cd34] (3+2/9) Accurately ripped
	 04     [59ea0b32|d8f7f890] (3+2/9) Accurately ripped
	 05     [ba26bc6f|107e8bd0] (3+2/9) Accurately ripped
	 06     [450aeeca|b3f9fbbe] (3+2/9) Accurately ripped
	 07     [eef9d6ed|9cba69d7] (3+2/9) Accurately ripped
	 08     [75bc1fa8|d7846bd7] (3+2/9) Accurately ripped
	 09     [c3830abc|6c38ed1b] (3+2/9) Accurately ripped
	 10     [3c6c1d96|68e8bd93] (3+2/9) Accurately ripped
	 11     [559661ae|3432056e] (3+2/9) Accurately ripped
	 12     [99ad4537|2ab689e9] (3+2/9) Accurately ripped
	 13     [925c2458|dea90549] (3+2/9) Accurately ripped
	 14     [5ae4616d|8d883981] (3+2/9) Accurately ripped
	 15     [5c50b853|e4e0d0b3] (3+2/9) Accurately ripped
	 16     [c6e438f2|88c2e2e6] (3+2/9) Accurately ripped
	 17     [04abe75c|8075fc3f] (3+2/9) Accurately ripped
	 18     [22242ab9|d4476f6a] (3+2/9) Accurately ripped
	 19     [faaaf059|a8b120ca] (3+2/9) Accurately ripped
	 20     [6087c48e|b3b2528a] (3+2/9) Accurately ripped
	Offsetted by -899:
	 01     [d57f7339] (4/9) Accurately ripped
	 02     [3e26b20c] (4/9) Accurately ripped
	 03     [339d9877] (4/9) Accurately ripped
	 04     [26be5ce4] (4/9) Accurately ripped
	 05     [0861719c] (4/9) Accurately ripped
	 06     [69180889] (4/9) Accurately ripped
	 07     [01a75f0a] (4/9) Accurately ripped
	 08     [16786c4c] (4/9) Accurately ripped
	 09     [9701e600] (4/9) Accurately ripped
	 10     [e92a6122] (4/9) Accurately ripped
	 11     [4afc1dca] (4/9) Accurately ripped
	 12     [0787ae87] (4/9) Accurately ripped
	 13     [7e06d0e4] (4/9) Accurately ripped
	 14     [251ec644] (4/9) Accurately ripped
	 15     [b72e8418] (4/9) Accurately ripped
	 16     [5efb9379] (4/9) Accurately ripped
	 17     [4a629a44] (4/9) Accurately ripped
	 18     [21195f81] (4/9) Accurately ripped
	 19     [356f1792] (4/9) Accurately ripped
	 20     [f20969c4] (4/9) Accurately ripped
	Offsetted by -938:
	 01     [8cdcdaa2] (0/9) No match (V2 was not tested)
	 02     [6e40e5e1] (0/9) No match (V2 was not tested)
	 03     [db22a1d4] (0/9) No match (V2 was not tested)
	 04     [f8b8ae1a] (0/9) No match (V2 was not tested)
	 05     [bd2dc04e] (0/9) No match (V2 was not tested)
	 06     [f15c2b5b] (0/9) No match (V2 was not tested)
	 07     [260f2603] (0/9) No match (V2 was not tested)
	 08     [2d1aeea0] (0/9) No match (V2 was not tested)
	 09     [f42fd674] (0/9) No match (V2 was not tested)
	 10     [d032593e] (0/9) No match (V2 was not tested)
	 11     [19d4ad36] (0/9) No match (V2 was not tested)
	 12     [2f9b1f97] (0/9) No match (V2 was not tested)
	 13     [62179e00] (0/9) No match (V2 was not tested)
	 14     [a5353daf] (0/9) No match (V2 was not tested)
	 15     [40644699] (0/9) No match (V2 was not tested)
	 16     [9a42ecd4] (0/9) No match (V2 was not tested)
	 17     [c4279c0c] (0/9) No match (V2 was not tested)
	 18     [e98689a9] (0/9) No match (V2 was not tested)
	 19     [86d8fbd8] (0/9) No match (V2 was not tested)
	 20     [878517a1] (0/9) No match (V2 was not tested)
	Offsetted by -902:
	 01     [1870a130] (0/9) No match (V2 was not tested)
	 02     [f7384e6e] (0/9) No match (V2 was not tested)
	 03     [b2666e73] (0/9) No match (V2 was not tested)
	 04     [24ac1437] (0/9) No match (V2 was not tested)
	 05     [b764de8f] (0/9) No match (V2 was not tested)
	 06     [4dd00bda] (0/9) No match (V2 was not tested)
	 07     [b5af5aa7] (0/9) No match (V2 was not tested)
	 08     [7aac4ef0] (0/9) No match (V2 was not tested)
	 09     [c58f4744] (0/9) No match (V2 was not tested)
	 10     [49b4d6ae] (0/9) No match (V2 was not tested)
	 11     [5ae563e6] (0/9) No match (V2 was not tested)
	 12     [45b08fd7] (0/9) No match (V2 was not tested)
	 13     [a3432f70] (0/9) No match (V2 was not tested)
	 14     [916f459b] (0/9) No match (V2 was not tested)
	 15     [c1bc7f5d] (0/9) No match (V2 was not tested)
	 16     [c6011080] (0/9) No match (V2 was not tested)
	 17     [c9e7e92c] (0/9) No match (V2 was not tested)
	 18     [1cd30049] (0/9) No match (V2 was not tested)
	 19     [d41f6396] (0/9) No match (V2 was not tested)
	 20     [e0ee5caf] (0/9) No match (V2 was not tested)
	Offsetted by 29:
	 01     [91e0e60e] (0/9) No match (V2 was not tested)
	 02     [6a8d08b3] (0/9) No match (V2 was not tested)
	 03     [60379f19] (0/9) No match (V2 was not tested)
	 04     [34d632dc] (0/9) No match (V2 was not tested)
	 05     [e8dd9b6f] (0/9) No match (V2 was not tested)
	 06     [1201063e] (0/9) No match (V2 was not tested)
	 07     [cd5756aa] (0/9) No match (V2 was not tested)
	 08     [57c690cc] (0/9) No match (V2 was not tested)
	 09     [ac2c5e80] (0/9) No match (V2 was not tested)
	 10     [ec8702a2] (0/9) No match (V2 was not tested)
	 11     [6672114a] (0/9) No match (V2 was not tested)
	 12     [96221887] (0/9) No match (V2 was not tested)
	 13     [d5149264] (0/9) No match (V2 was not tested)
	 14     [43da3d24] (0/9) No match (V2 was not tested)
	 15     [f64990b8] (0/9) No match (V2 was not tested)
	 16     [e3048059] (0/9) No match (V2 was not tested)
	 17     [33f89744] (0/9) No match (V2 was not tested)
	 18     [4b771881] (0/9) No match (V2 was not tested)
	 19     [637fe8be] (0/9) No match (V2 was not tested)
	 20     [ed7e5e78] (0/9) No match (V2 was not tested)
	
	Track Peak [ CRC32  ] [W/O NULL] [  LOG   ]
	 --  100.0 [26634C66] [38A24B8E]           
	 01   98.4 [178D1D4E] [D7F0CE76]   CRC32   
	 02   93.0 [EBBEBBAC] [0BEF2CF4]   CRC32   
	 03   99.9 [6E55ED6B] [FA89B8D1]   CRC32   
	 04   99.3 [8241C799] [9E22EFF2]   CRC32   
	 05   98.1 [AD0D000C] [6EF4FAFF]   CRC32   
	 06   98.9 [0F82AF9E] [409D65E4]   CRC32   
	 07   97.9 [21AE2A5A] [127644FE]   CRC32   
	 08   98.8 [495C8FC4] [1C7A6854]   CRC32   
	 09   98.9 [A0881C86] [263D51F1]   CRC32   
	 10   97.3 [6874CCAE] [53C884D6]   CRC32   
	 11   98.5 [2AAF505A] [AE15BCC3]   CRC32   
	 12   99.2 [297223B5] [87D43DBB]   CRC32   
	 13   99.9 [69297F6C] [6C839606]   CRC32   
	 14   89.1 [F5BA960F] [3C8CF129]   CRC32   
	 15   98.5 [DC77F089] [F3A8120A]   CRC32   
	 16   99.5 [6FEEF67D] [C1F10BA4]   CRC32   
	 17  100.0 [5E51C2AE] [F3390264]   CRC32   
	 18   94.6 [36F7471F] [E5C076EA]   CRC32   
	 19   75.8 [11C7C7D4] [09B2CDF1]   CRC32   
	 20   87.4 [FE5E210D] [46805784]   CRC32   
	 
	 

What is really nice about this windows command line tool, is that not only it verifies using the AccurateRip database, but in addition it does a second verification using [CUETools database](http://cue.tools/wiki/CUETools_Database).

After many trials and errors, I ended up using this tool because I trust it more comparing to the first method. I have also created a very small script (it's actually not a script, but one command - you can also create an alias for that) which I use in order to store a log inside each folder of my music library

	wine /home/your_username/cuetools/ArCueDotNet.exe *.cue > cuetools.log

