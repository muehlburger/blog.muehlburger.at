---
title: Enable HTTPS everywhere
author: Herbert Mühlburger
type: post
date: 2014-01-05T15:35:26+00:00
url: /2014/01/enable-https-everywhere/
bitcointips_address:
  - 1MvtCTpySxfJWUm4KATMH6ELFC8ryMPgux
categories:
  - Computer Science
  - HowTo
  - Technology
tags:
  - 30C3
  - Crypto
  - Encryption
  - How To
  - HTTPS
  - SSL
  - TLS
  - video

---
<figure id="attachment_1847" style="width: 928px" class="wp-caption aligncenter">[<img class="size-full wp-image-1847" alt="SSL-Report for blog.muehlburger.at" src="https://blog.muehlburger.at/wp-content/uploads/2014/01/SSL-Report.png" width="928" height="505" srcset="https://blog.muehlburger.at/wp-content/uploads/2014/01/SSL-Report.png 928w, https://blog.muehlburger.at/wp-content/uploads/2014/01/SSL-Report-300x163.png 300w" sizes="(max-width: 709px) 85vw, (max-width: 909px) 67vw, (max-width: 1362px) 62vw, 840px" />][1]<figcaption class="wp-caption-text">SSL-Report for blog.muehlburger.at</figcaption></figure> 

Finally I finished to configure my <a title="Hypertext Transfer Protocol Secure" href="https://en.wikipedia.org/wiki/HTTP_Secure" target="_blank">HTTPS</a> protocol support for <a title="https://blog.muehlburger.at" href="https://blog.muehlburger.at" target="_blank">blog.muehlburger.at</a>. Supporting encrypted communication is an important part of the internet today. Everybody should support encrypted communication on the web. A good resource on how to select strong cypher suites and to configure your web server to support encryption properly is <a title="https://bettercrypto.org" href="https://bettercrypto.org" target="_blank">bettercrypto.org</a>.

There is also a great video covering the current state of the art in crypto held by security researchers at <a title="https://events.ccc.de/congress/2013/wiki/Main_Page" href="https://events.ccc.de/congress/2013/wiki/Main_Page" target="_blank">30C3</a>:



I configured <a title="nginx" href="http://nginx.org/" target="_blank">nginx</a> to support encrypted communication exclusively for my <a title="WordPress" href="https://en.wikipedia.org/wiki/WordPress" target="_blank">WordPress</a> installation. The <a title=" https://bettercrypto.org/static/applied-crypto-hardening.pdf" href=" https://bettercrypto.org/static/applied-crypto-hardening.pdf" target="_blank">PDF guide from bettercrypto.org</a> was a great resource for selecting the cypher suits and some additional parameters.

If you would like to configure your nginx webserver and WordPress installation to support https just drop me a message. I am pleased to help you with my experiences.

(via <a title="30C3 - A year in Crypto" href="http://media.ccc.de/browse/congress/2013/30C3_-_5339_-_en_-_saal_1_-_201312281830_-_the_year_in_crypto_-_nadia_heninger_-_djb_-_tanja_lange.html" target="_blank">A year in Crypto</a>)

 [1]: https://blog.muehlburger.at/wp-content/uploads/2014/01/SSL-Report.png