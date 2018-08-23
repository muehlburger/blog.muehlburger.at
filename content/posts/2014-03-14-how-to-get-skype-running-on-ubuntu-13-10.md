---
title: How to get Skype running on Ubuntu 13.10
author: Herbert Mühlburger
type: post
date: 2014-03-14T10:30:08+00:00
url: /2014/03/how-to-get-skype-running-on-ubuntu-13-10/
bitcointips_address:
  - 1FVkv1YbDFsSCfAAGsZULyYbDFytdjCkSP
categories:
  - HowTo

---
I got <a href="http://www.skype.com" title="Skype" target="_blank">Skype</a> running on <a href="http://www.ubuntu.com" title="Ubuntu" target="_blank">Ubuntu 13.10</a> using the following commands:

[code lang=&#8221;bash&#8221;]
  
sudo -s
  
mv /usr/bin/skype /usr/bin/skype-bin
  
emacs /usr/bin/skype
  
[/code]

Filling the file with the following content:

[code lang=&#8221;bash&#8221;]
  
#!/bin/sh
  
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
  
exec skype-bin
  
[/code]

Don&#8217;t forget to change the file mode:
  
[code lang=&#8221;bash&#8221;]
  
chmod 0755 /usr/bin/skype
  
[/code]

(via <a href="http://ubuntuforums.org/showthread.php?t=2139202" title="timgood" target="_blank">timgood</a>)