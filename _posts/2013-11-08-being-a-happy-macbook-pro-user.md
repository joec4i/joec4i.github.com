---
layout: post
title: "Being a Happy Macbook Pro User"
description: ""
category: "mac"
tags: [mac]
---
{% include JB/setup %}

I have been a Thinkpad user for years. My first Thinkpad was an IBM Thinkpad T60. I wasn't all happy with it but I did like its track point very much. And that's probably why I bought another Thinkpad, Lenovo Thinkpad T410, 3 years ago as an upgrade. On the T60 I ran Linux as the desktop system from day one. I'd tried various distributions including debian, Ubuntu and ArchLinux. I was generally happy with Linux back then before Unity and Gnome shell were introduced and when font rendering was way better in Linux than in Windows XP thanks to Xft. But then the desktop was often changed drastically after each new Ubutun release, and I became sick of having to fix this and that while trying to get used to the new UI. So after running Ubuntu on my T410 for about a year, I decided to switch to Windows 7. It was fine: its GUI is generally stable and efficient; it has much better support for QQ and some other software commonly used in China; and it gives my laptop better battery life. However, cmd.exe sucks! So from time to time I had to either use cygwin or ssh to a guest Linux system running inside Virtualbox, just so I could run something from cli.

So basically Mac OS X is what I need -- an operating system with a decent GUI and a real terminal that supports Unix shell scripting. As my T410 is growing outdated and Apple recently released its new Macbook Pro, I decided to buy one. Last week I picked the 13inch MacBook Pro with Retina from a local dealer who ordered the laptop from Hong Kong for me. I had to make the purchase from him because the new MacBook Pro had not been available on the Chinese mainland market.

**The Hardware**

Although it's not quite fair to make a comparison between my old Thinkpad T410 and the new Macbook Pro, I have to say that the industrial design of the Macbook Pro has gone far ahead of that of the Thinkpad. Thinkpad is yet another laptop with good quality, but the RMBP is what can be called an artwork. It's thin, "designed", polished, and ... aluminum. I particularly like the trackpad and the back light under the keyboard although it took me some time to get used to them. The MBP keyboard has a shorter travel distance that the thinkpad keyboard. Longer keyboard travel distance is better but after two day's usage I find I'm quite used to the new keyboard, so no complaints on that. The trackpad, on the other hand, is suprisingly easy to use. Its multi-touch gesture support makes it quite convenient to move around the system. That makes the trackpad a better alternative to the trackpoint, in my opinion. 

The retina screen is also spenlendid and something that has to be mentioned. As a web engineer and a Linux sysadmin, I spend a lot of time reading and writing text-based content. I used to hate the Mac Terminal.app mostly because the default font makes the terminal looks crappy. But the retina screen makes text reading a wonderful experience and now I simply love using Terminal.app. I have an ipad with a retina screen, which is also good for text rendering, but an 13 inch screen makes it even better. Although I regret a bit that I didn't choose the 15inch MBP, the current one is good enough for me. I think every programmer should get a retina screen for work, and that should be even more important than getting a good chair:)

Battery life is another amazing feature that comes with the Macbook Pro. Although I can't really have it run 9 hours as stated in the specification, which is probabaly because I always have a lot of services running in the background, 5-6 hours is sufficient for me. Now I don't have to worry about finding the charger the moment I open my laptop.

If there's anything I should complain about the MBP, it's the lack of the ethernet port. In order to make the Macbook thinner, Apple decided to remove the ethernet port and replace it with two thunderbolt ports. Since I need a more reliable and faster network connection than wifi in the office, I had to buy a thunderbolt-to-ethernet adapter. The adapter can get heated easily, and I have a feeling that it might be more power-consuming than the built wifi. The later one might be just a delusion though.

Overall, I think the MBP is a way better laptop than other laptops I have ever used. The price is also quite acceptable, considering that it has a retina screen and such a marvelous design, and the fact that many people in China are spending $1000 on an iphone. Of course, for those who can't work with the OS X, MBP won't be the right choice.

####The Software

Apple has made its iWork suite free which is quite good news. I have installed all of them but so far I haven't used them very much. But I think Pages and Keynote will be helpful in the future.

**MacPorts, homebrew or fink?**

I'm a heavy command line user, so I needed to decide which package manager to use. MacPorts, homebrew and fink were on the table. It appears fink is a bit outdated. I tried homebrew first, but soon I realized that it has much less packges than MacPorts does. Despite the fact that many people recommend homebrew over MacPorts and that MacPorts is painfully slow in China, I decided that MacPorts is right for me. And it is. The MacPorts repository has almost all the packages I need. And I like `port load` and `port unload` very much, because launchctl is way more inconvenient to use.

After a bit of configuration tweaking, I finally got MacPorts work at an acceptable speed. Basically what I did was: 1) use a Chinese mirror site for base.tar and ports.tar; 2) disable port from attempting to download from archives sites, because in China downloading form an arhieves site is painfully slow and most likely fails; 3) for distfiles, make MacPorts download from the mirror in Italy. 

**Browsers**

I've been using firefox as my default browser for many years. I'm used to the same set of extensions, including Foxyproxy, livehttpheaders, web developer and a few others. Firefox is not all perfect, but I think I'll keep the habit of using it for a long time. Luckily with the help of Firefox Sync, it was quite easy to migrate most of my browser configuration from the old laptop to the new one. 

**Terminal.app**

I used to hate Terminal.app as I mentioned above. But with the retina screen, I suddenly find it quite pleasant to use. So I decided not to try iTerm2 as a replacement. There were a few minor problems, but I managed to solve them really quickly. 


**The Dictionary**

I'm not a native English speaker. Every now and then I will need the help of an English dictionary. On windows I use this program called LDOCE5 Viewer to query English words from the Longman Dictionary of Contemporary English 5th Edition which I think is the best dictionary I've known. But unfortunately there's no Mac version of this program. However, the viewer is written in python and is open source. So I figure I might be able to get it running under OS X. Amazingly, it worked. I reported that on github. The author quickly added a few improvements. By the next day we have a Mac version of LDOCE5 Viewer on https://hakidame.net/ldoce5viewer/download . The author @ciscorn is a really good programmer. He managed to write Mac-specific code under Windows/Linux. And the code just worked. I was really impressed. Anyway, I'm glad I can continue using LDOCE5 on Mac.


**iBook**

Most of the time I use kindle for reading. But now on the 13inch retina screen reading on iBook is quite pleasant too. It's a shame that I can't rotate the screen like the iPad though. 

**Something Else**

Most software I use already have Mac versions, such as QQ, skype, virtualbox and eclipse. Many software made by Chinese vendors tend to have annoying popups or embedded banners, e.g. QQ, sohu tv and xunlei. But their Mac versions are clean, which is a bonus to me. 

On windows I use tunnelier to maintain ssh tunnel connections so that I can visit websites blocked by GFW. The alternative I found is SSH Tunnel Manager. I can simply use the `ssh -D` command but a connection manager does save some time for me. Also, I use Tunnelblick for vpn connection management, and CoRD as a replacement for mstsc.exe or rdesktop.

I find Calendar very handy too. I used to maintain my todo list with a simple notes app. But now I like using Calendar more.
