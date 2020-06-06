+++
author = "giannoug"
date = 2015-08-23T12:03:11Z
description = ""
draft = false
image = "/images/2015/08/bonjour.jpg"
slug = "install-bonjour-to-windows-without-itunes"
title = "Install Bonjour to Windows without iTunes"

+++


Lately I've been messing around with Zero-configuration networking (aka Zeroconf) services, mostly because I wish to employ some WiFi modules around the house. There is a problem though, how can I discover what's a device's IP address without poking at the DHCP server's client list and without setting a static IP for each of the modules? I would also prefer to "discover" such nodes and be able to "hot swap" them without altering static IPs, MAC addresses and all that stuff.

Arduino for ESP8266, the software and hardware which I am using for the modules has a built-in library that supports mDNS/DNS-SD requests. Most Linux distros, *BSDs and Apple devices have built-in support for zero-configuration networking, something Windows is unfortunately lacking.

I don't really like extra software and I personally can't find a use for iTunes. The only way to get Bonjour, Apple's implementation of Zero-configuration networking, to install on Windows is by installing iTunes and some extra useless programs. What if you don't need that extra stuff and/or iTunes altogether? To be honest, I don't even want to run the iTunes installer to check if there is an option to only install Bonjour or some other software.

Luckily, the iTunes installer (at least the x64 version) is a self-extracting archive containing many different installation programs for each bundled component. So, if you have WinRAR/7z installed, you can extract the "archive" and get the "Bonjour64.msi" installer. Running it will only install Bonjour on your computer.

Phew.

As you might imagine, you will probably lose the auto update functionality, because Apple Updater or whatever is called is not installed. Its ok for me, I can live with it, as long as I know what's installed on my computer.

