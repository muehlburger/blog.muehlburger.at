---
title: How to convert a .PDF file to .PNG using Image Magick
author: Herbert Mühlburger
type: post
date: 2016-03-31T08:27:56+00:00
url: /2016/03/how-to-convert-a-pdf-file-to-png-using-image-magick/
categories:
  - HowTo
tags:
  - convert
  - image converstion
  - image manipulation

---
<a href="http://www.imagemagick.org" target="_blank">ImageMagick</a> is a powerfull tool to manipulate images. If you want to convert a .PDF to an .PNG file use the following command:

`convert -verbose -density 300 -trim input.pdf -quality 100 -sharpen 0x1.0 -background white -flatten output.png`

Assuming that your pdf is called &#8220;input.pdf&#8221; and consists only of one page. The above command colors any transparent background white.

(via <a href="http://stackoverflow.com/questions/6605006/convert-pdf-to-image-with-high-resolution" target="_blank">stackoverflow.com</a> and <a href="https://imagemagick.org/discourse-server/viewtopic.php?t=22275#p92703" target="_blank">imagemagick.org</a>)