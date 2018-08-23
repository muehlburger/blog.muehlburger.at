---
title: How to install (Oracle) Sun Java SDK 1.6.x (Java 6) on Ubuntu
author: Herbert Mühlburger
type: post
date: 2011-01-10T20:45:32+00:00
url: /2011/01/how-to-install-oracle-sun-java-sdk-1-6-x-java-6-on-ubuntu/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
dsq_thread_id:
  - "246432719"
bitcointips_address:
  - 1KAwt4N8CTr2abW72Zbs21ux85jXtX2CHh
categories:
  - Computer Science
  - Programming
tags:
  - How To
  - Installation
  - Instruction
  - Java
  - Java Development Kit
  - Oracle
  - Programming
  - Sun
  - tutorial
  - Ubuntu

---
Dieser Beitrag beschreibt die Installation des Sun Java SDK 1.6.x on Ubuntu (Maverick). The English explanation on how to install Sun Java SDK 1.6.x can be found <a title="http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/#sun-java-6" href="http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/#sun-java-6" target="_blank">here</a>.

### Canonical-Partner Repositories aktivieren:

Dies geschieht unter &#8220;System&#8221; -> &#8220;Systemverwaltung&#8221; -> &#8220;Synaptic Paketverwalung&#8221;. In der Paketverwaltung finden sich die Paketquellen unter dem Menüpunkt &#8220;Einstellungen&#8221;. In den Einstellungen wechselt man auf den Reiter &#8220;Andere Software&#8221; und aktiviert dort &#8220;Canonical-Partner&#8221; bzw. &#8220;Canonical-Partner (Quelltext)&#8221;.  Nach dem Klick auf &#8220;Schließen&#8221; werden die Paketlisten neu geladen.

### Terminal öffnen und Java 6 JDK installieren:

[sourcecode]
  
$ sudo apt-get install sun-java6-jdk
  
[/sourcecode]

### Java Version zur Standardversion auf dem System machen:

[sourcecode]
  
$ sudo update-java-alternatives -s java-6-sun
  
[/sourcecode]

Für das aktuelle Java Development Kit wird der Symlink <tt>/usr/lib/jvm/java-6-sun</tt> erstellt. Dieser zeigt auf die aktuell installierte Version des JDK.

### Installation überprüfen:

[sourcecode]
  
user@ubuntu:~# java -version
  
java version "1.6.0_22"
  
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
  
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)
  
[/sourcecode]

Damit ist die Installation abgeschlossen.

Vielen Dank an Michael Noll für die <a title="englische Anleitung" href="http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/#sun-java-6" target="_blank">englische Installationsanleitung</a>, die ich als Vorlage verwendet habe.

### Weitere Artikel {.zemanta-related-title}

<ul class="zemanta-article-ul">
  <li class="zemanta-article-ul-li">
    <a href="http://www.twm-kd.com/computers/software/installing-sun-java6-in-ubuntu-maverick-meerkat/">Installing sun-java6 in Ubuntu Maverick Meerkat</a> (twm-kd.com)
  </li>
  <li class="zemanta-article-ul-li">
    <a href="http://www.techeye.net/software/oracles-open-source-java-for-mac-os-x-built">Oracle&#8217;s Open Source Java for Mac OS X built</a> (techeye.net)
  </li>
</ul>