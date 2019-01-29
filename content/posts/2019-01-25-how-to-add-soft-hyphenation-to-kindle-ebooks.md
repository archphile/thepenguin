+++
title = "How to add soft hyphenation in Kindle e-books"
date =  "2019-01-25"
categories = ["General"]
tags = ["kindle", "hyphenation", "calibre", "Hyphenate This!"]
+++

One of the major "issues" with kindle, is how much its hyphenation capabilities suck, especially, when an e-book is not specifically made for kindle and it's converted from an .epub file(as most of my e-books are).

However, the community (**SauliusP** to be more specific) gave a solution to this, with a [calibre](https://calibre-ebook.com/) plugin named [Hypenate This!](https://www.mobileread.com/forums/showthread.php?t=208534)

## Installation

1. [Download](https://www.mobileread.com/forums/showthread.php?t=208534) and install the plugin in calibre:

		Preferences -> Plugins -> Load plugin from file
	
2. Download a [hyphenation dictionary](https://extensions.libreoffice.org/extensions/english-new-zealand-dictionary-hyphenation-thesaurus)

3. Add the dictionary to Hyphenate This! plugin:

		Hyphenate (top toolbar) -> Settings -> Add dictionary (oxt or dic)
	
## Procedure

Let's say that we have an e-book in **.epub** format and we want to prepare it for our kindle. The procedure we have to follow is the following:

1. Add the epub to calibre (by just dragging and dropping it)

2. Press the **Convert Books** (top toolbar) button and convert the e-book to **.azw3** format

3. Select the e-book from the list and press the **Hyphenate button** (top toolbar)

4. Select the **AZW3** option and press **OK**


After the steps above, our e-book is ready to be transferred to kindle.