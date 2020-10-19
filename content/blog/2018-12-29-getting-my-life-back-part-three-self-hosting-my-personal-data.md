+++
title = "Getting my life back, Part III - Self-hosting my personal data (contacts, bookmarks, passwords, calendar, notes, tasks)"
date =  "2018-12-29"
categories = ["Productivity"]
tags = ["contact management", "password management", "calendar", "Nextcloud", "GTD", "Simpletask", "Notes", "Keepass2android", "DAVdroid"]
+++

This third part of the series "Getting my life back", is about **personal data privacy**. Although it's a huge topic, I will just try to give some further details on how I manage my personal data, after of course having already [got rid of my social media accounts]({{< ref "2018-12-27-getting-my-life-back-part-one-social-media.md" >}}), one of the most dangerous personal privacy leaks.

In addition to that, on my previous post about [smartphone addiction]({{< ref "2018-12-28-getting-my-life-back-part-two-smartphone-addiction.md" >}}), I mentioned that my smartphone now serves me only as a means for better productivity. In this guide, you will find out how!

**Note:** Whenever the term **"productivity"** is used in this blog, this **doesn't mean** becoming a better employee, manager, businessman etc.. By seeing things from a different perspective, productivity is a "tool" (to be more specific, a procedure with the use of an efficient tool-set) that assists one to finish with all the usual responsibilities (including one's job) ASAP - using special tools and techniques - and have as much time as possible to spend on everything else (hobbies, art, knowledge, quality time with family and friends etc.).


## Before you proceed with this post

In the previous posts I have already mentioned how I use my own cloud with [Nextcloud]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}}).

I have also written two posts on **GTD**, one [providing information]({{< ref "2018-06-06-how-to-use-a-simple-text-based-todo-list-to-get-things-done.md" >}}) about [Todo.txt](http://todotxt.org/) and a second one describing [how exactly I GTD]({{< ref "2018-09-26-how-i-GTD.md" >}}).

I suggest you to at least have a look at these articles in order to understand the context of this post.


## Contacts

For my contacts on Android, I used to sync using Google Contacts for years. After setting up [Nextcloud]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}}), I decided to stop letting Google know who I know and self-host them. For this reason I now use:

- [Nextcloud Contacts](https://github.com/nextcloud/contacts#readme) to which I imported/edited/etc my exported Gmail contacts

- [DAVx⁵](https://f-droid.org/en/packages/at.bitfire.davdroid/) to sync contacts between my Android Smartphone and my [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})



## Bookmarks

For bookmark syncing I use:

- [Nextcloud Bookmarks](https://github.com/nextcloud/bookmarks)

along with

- [Nextcloud Bookmarks for Android](https://f-droid.org/en/packages/org.schabi.nxbookmarks/)

and

- [Floccus addon](https://addons.mozilla.org/el/firefox/addon/floccus/) for Firefox.


For the record, I don't sync all my bookmarks. I just use the above combo to create a "shared folder" of bookmarks between my Desktop PC and the smartphone.



## Password Management

For passwords I use:

- [KeePassXC](https://keepassxc.org/),  with the database stored on a Nextcloud folder, automatically synced with [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})

- [Keepass2Android](https://github.com/PhilippC/keepass2android) on my smartphone which accessess the same database stored on the [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})



## Calendar

For this purpose I use:

- [Nextcloud Calendar](https://github.com/nextcloud/calendar/)

along with 

- [DAVx⁵](https://f-droid.org/en/packages/at.bitfire.davdroid/) to sync the calendar between my Android Smartphone and my [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})

and

- [Simple Calndar Pro](https://f-droid.org/en/packages/com.simplemobiletools.calendar.pro/) to manage the synced calendar on the smartphone



## Note Keeping

Note keeping is a very important part of my [GTD system]({{< ref "2018-09-26-how-i-GTD.md" >}}). For this purpose I use:

- [QOwnNotes](https://www.qownnotes.org/) on my desktop PC, with the notes (.txt files) stored on a Nextcloud folder, automatically synced with the [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})

- [Notes](https://github.com/nextcloud/notes) for Nextcloud

along with

- [Notes](https://f-droid.org/en/packages/it.niedermann.owncloud.notes/) for Android



## Tasks

For my **GTD** system I use:

- [Qtodotxt](http://qtodotxt.org/) on my desktop PC, reading **todo.txt** and **done.txt** from a Nextcloud folder automatically synced with the [Nextcloud server]({{< ref "2018-06-17-how-to-set-up-your-own-cloud-using-nextcloud-on-archlinux" >}})

- [Simpletask for Nextcloud](https://github.com/mpcjanssen/simpletask-android) on my smartphone

**Note:** Please refer to **"Before you proceed with this post"** section of this article for further information about this section.



## Conclusion

It's obvious that having my own cloud infrastructure made the transition to self-hosting all my personal data a very easy task. 

This way I ensure (as much as I can) that no third party will have access on the people I know, services I use, stuff I do etc.

However, it doesn't mean that self-hosting this information provides better security. 

A Nextcloud server requires a Linux machine with various services running on it and one **should take care of its configuration** to make it as secure as possible.
