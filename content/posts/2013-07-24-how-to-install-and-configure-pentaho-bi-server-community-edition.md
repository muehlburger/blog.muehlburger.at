+++
author = "Herbert Mühlburger"
categories = ["Business Intelligence", "Computer Science", "Pentaho"]
date = "-001-11-30T00:00:00+00:00"
draft = true
tags = ["BI", "Business Intelligence", "Pentaho"]
title = "How to install and configure Pentaho BI Server Community Edition"
type = "post"
url = "/?p=1705"

+++
The following steps are some notes that I took on installing and configuring Pentaho BI Server Community Edition (Pentaho BI Suite 4.8) on CentOS using MySQL as Database backend.

Download Pentaho BI Server:

[code language=&#8221;bash&#8221;]
  
wget http://sourceforge.net/projects/pentaho/files/Business%20Intelligence%20Server/4.8.0-stable/biserver-ce-4.8.0-stable.tar.gz
  
[/code]

Extract the archive file:

[code language=&#8221;bash&#8221;]</span>
  
tar xzfv biserver-ce-4.8.0-stable.tar.gz
  
[/code]

Download MySQL Schemas from http://www.prashantraju.com/projects/pentaho/:
  
[code language=&#8221;bash&#8221;]
  
tar xzfv biserver-ce-4.8.0-stable.tar.gz
  
[/code]

Configuring JDBC security:
  
Edit the following files:

[code language=&#8221;bash&#8221;]
  
emacs applicationContext-spring-security-jdbc.xml
  
[/code]