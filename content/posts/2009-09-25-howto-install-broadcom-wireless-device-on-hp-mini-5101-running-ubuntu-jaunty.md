+++
aktt_notify_twitter = ["yes"]
aktt_tweeted = ["1"]
author = "Herbert Mühlburger"
bitcointips_address = ["1QKg7vMB1WRdsSsxtsG8SSL6ztZ9K5nrsb"]
categories = ["Computer Science"]
date = "2009-09-25T17:31:37+00:00"
dsq_thread_id = ["246421102"]
tags = ["Distributions", "Hewlett-Packard", "HP Mini 5101", "Installation", "Linux", "Netbook", "Operating system", "SUSE Linux", "SUSE Linux Enterprise Desktop", "Ubuntu"]
title = "How to install Broadcom Wireless Device on HP Mini 5101 running Ubuntu Jaunty"
type = "post"
url = "/2009/09/howto-install-broadcom-wireless-device-on-hp-mini-5101-running-ubuntu-jaunty/"

+++
<div class="mceTemp mceIEcenter">
  <dl id="attachment_538" class="wp-caption aligncenter" style="width: 440px;">
    <dt class="wp-caption-dt">
      <img class="size-large wp-image-538" title="HP Mini 5101" src="http://178.79.139.40/wp-content/uploads/2009/09/hp-mini-copyright-hp-430x343.jpg" alt="HP Mini 5101" width="430" height="343" />
    </dt>
  </dl>
</div>

Yesterday I received my new **<a class="zem_slink" title="Hewlett-Packard" rel="homepage" href="http://www.hp.com">HP</a> Mini 5101** running <a class="zem_slink" title="SUSE Linux Enterprise Desktop" rel="wikipedia" href="http://en.wikipedia.org/wiki/SUSE_Linux_Enterprise_Desktop">Suse Linux Enterprise Desktop</a> 11 (SLED 11). Due to the fact, that i do not like working with Suse I installed <a title="Ubuntu 9.04" href="http://www.ubuntu.com/" target="_blank">Ubuntu 9.04</a> but there were some problems regarding the wireless chipset (<a class="zem_slink" title="Broadcom" rel="homepage" href="http://www.broadcom.com/">Broadcom</a> 5343) and the <a class="zem_slink" title="Ethernet" rel="wikipedia" href="http://en.wikipedia.org/wiki/Ethernet">Ethernet</a> adapter (Marvel 436c).

After installation the wireless and the ethernet devices were not working. The problem was that I needed to install proprietary drivers which were not included in Ubuntu due to licence issues. Probably you don&#8217;t have internet connection as I didn&#8217;t have. I had to download the packages on another computer and transfer them via a <a class="zem_slink" title="Universal Serial Bus" rel="wikipedia" href="http://en.wikipedia.org/wiki/Universal_Serial_Bus">USB</a> stick to my **HP Mini 5101**:

The packages to install are the following:

  1. <a title="linux-image-2.6.28-15-generic" href="http://packages.ubuntu.com/jaunty-updates/linux-image-2.6.28-15-generic" target="_blank">linux-image-2.6.28-15-generic</a>
  2. <a title="http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-15-generic" href="http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-2.6.28-15-generic" target="_blank">linux-backports-modules-2.6.28-15-generic</a>
  3. <a title="linux-backports-modules-jaunty-generic" href="http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty-generic" target="_blank">linux-backports-modules-jaunty-generic</a>
  4. <a title="linux-backports-modules-jaunty" href="http://packages.ubuntu.com/jaunty-updates/linux-backports-modules-jaunty" target="_blank">linux-backports-modules-jaunty</a>
  5. <a title="linux-restricted-modules-common" href="http://packages.ubuntu.com/jaunty/misc/linux-restricted-modules-common" target="_blank">linux-restricted-modules-common</a>
  6. <a title="linux-restricted-modules-2.6.28-15-generic" href="http://packages.ubuntu.com/jaunty/i386/linux-restricted-modules-2.6.28-15-generic" target="_blank">linux-restricted-modules-2.6.28-15-generic</a>

After downloading, installing and rebooting my system the proprietary drivers could be activated in _System -> Administration -> Hardware Drivers_ and everything worked fine.

###### Related articles by Zemanta {.zemanta-related-title}

<ul class="zemanta-article-ul">
  <li class="zemanta-article-ul-li">
    <a href="http://techie-buzz.com/linux-tips/how-to-install-skype-ubnutu.html?utm_source=subscriber&utm_medium=rss&utm_campaign=rss">How to Install Skype in Ubuntu</a> (techie-buzz.com)
  </li>
  <li class="zemanta-article-ul-li">
    <a href="http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/">How To Create An Ubuntu Installation USB On The Mac</a> (makeuseof.com)
  </li>
  <li class="zemanta-article-ul-li">
    <a href="http://maketecheasier.com/install-and-use-ubuntu-netbook-remix/2009/09/22">How to Install and Use Ubuntu Netbook Remix</a> (maketecheasier.com)
  </li>
</ul>

<div class="zemanta-pixie">
  <a class="zemanta-pixie-a" title="Reblog this post [with Zemanta]" href="http://reblog.zemanta.com/zemified/6e2eff7c-cbe3-4151-b337-bbaf7e48b234/"><img class="zemanta-pixie-img" src="http://img.zemanta.com/reblog_e.png?x-id=6e2eff7c-cbe3-4151-b337-bbaf7e48b234" alt="Reblog this post [with Zemanta]" /></a><span class="zem-script more-related pretty-attribution"></span>
</div>