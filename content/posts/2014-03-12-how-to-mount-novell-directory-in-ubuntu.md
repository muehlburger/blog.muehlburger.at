---
title: How to mount Novell directory in Ubuntu
author: Herbert Mühlburger
type: post
date: 2014-03-12T14:04:18+00:00
url: /2014/03/how-to-mount-novell-directory-in-ubuntu/
bitcointips_address:
  - 167DCfB9qHD92UppDFZj6X3ytPaY2fsxbm
categories:
  - HowTo
tags:
  - How To
  - mount
  - ncpfs
  - ncpmount
  - novell
  - Ubuntu

---
First you have to install ncpfs using apt-get:

[code language=&#8221;bash&#8221;]
  
sudo apt-get install ncpfs
  
[/code]

Then mount your novell directories using the following commands:

[code language=&#8221;bash&#8221;]
  
mkdir /media/novell
  
sudo chown <localuser>:<localgroup> /media/novell
  
sudo ncpmount -S <name-of-netware-server> -A <fully-qualified-name-of-server-or-ip-address> -U <novellusername-using-dot-notation> -u <localusername> -g <localgroup> -o nfsextras,symlinks,tcp,rw /media/novell -p cp850 -y utf8
  
[/code]

This will mount all of the volumes. If you wish to mount a specific volume use the -V option.

Having issues? Just drop me a line.