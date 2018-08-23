---
title: HowTo set up the Android SDK on Ubuntu for HTC Phones
author: Herbert Mühlburger
type: post
date: 2011-03-12T18:19:18+00:00
url: /2011/03/howto-set-up-the-android-sdk-on-ubuntu-for-htc-phones/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "252252883"
aktt_tweeted:
  - "1"
bitcointips_address:
  - 14tB5SAv5ztRNhNoLNVhCAoMmznq3Zm7TY
categories:
  - Android
  - Computer Science
  - Programming
tags:
  - Android
  - Android SDK
  - Eclipse
  - htc
  - HTC Corporation
  - Operating system
  - Ubuntu

---
<div class="zemanta-img">
  <figure style="width: 122px" class="wp-caption alignright"><a href="http://www.crunchbase.com/company/htc"><img title="Image representing HTC as depicted in CrunchBase" src="http://www.crunchbase.com/assets/images/resized/0001/9198/19198v2-max-450x450.png" alt="Image representing HTC as depicted in CrunchBase" width="122" height="71" /></a><figcaption class="wp-caption-text">Image via CrunchBase</figcaption></figure>
</div>

In this post I will explain how I set up the <a class="zem_slink" title="Android SDK" rel="homepage" href="http://developer.android.com/sdk/index.html">Android SDK</a> on Ubuntu for my <a title="HTC Desire" href="http://www.htc.com/de/product/desire/overview.html" target="_blank">HTC Desire</a>.

I first followed the steps for Ubuntu as described in <a title="Setting up a Device for Development" href="http://developer.android.com/guide/developing/device.html#setting-up" target="_blank">Setting up a Device for Development</a>:

> With an Android-powered device, you can develop and debug your Android applications just as you would on the emulator. Before you can start, there are just a few things to do:
> 
>   1. Declare your application as &#8220;debuggable&#8221; in your Android Manifest.In Eclipse, you can do this from the **Application** tab when viewing the Manifest (on the right side, set **Debuggable** to _true_). Otherwise, in the `AndroidManifest.xml` file, add `android:debuggable="true"` to the `<application>` element.
>   2. Turn on &#8220;USB Debugging&#8221; on your device.On the device, go to the home screen, press **MENU**, select **Applications** > **Development**, then enable **USB debugging**.
>   3. Setup your system to detect your device. 
>       * If you&#8217;re developing on <a class="zem_slink" title="Ubuntu (operating system)" rel="homepage" href="http://www.ubuntu.com/">Ubuntu Linux</a>, you need to add a rules file that contains a USB configuration for each type of device you want to use for development. Each device manufacturer uses a different vendor ID. The example rules files below show how to add an entry for a single vendor ID (the HTC vendor ID). In order to support more devices, you will need additional lines of the same format that provide a different value for the `SYSFS{idVendor}` property. For other IDs, see the table of [USB Vendor IDs][1], below. 
>           1. Log in as root and create this file: `/etc/udev/rules.d/51-android.rules`.For Gusty/Hardy/Maverick Meerkat, edit the file to read:
  
>             `SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"`</p> 
>             For Dapper, edit the file to read:
  
>             `SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0bb4", MODE="0666"`</li> 
>             
>               * Now execute:
  
>                 `chmod a+r /etc/udev/rules.d/51-android.rules`</ol> </li> </ul> </li> </ol> 
>             
>             You can verify that your device is connected by executing `adb devices` from your SDK `platform-tools/` directory. If connected, you&#8217;ll see the device name listed as a &#8220;device.&#8221;</blockquote> 
>             
>             When I executed **_adb devices_** the name of my HTC Desire just looked like &#8220;??????????&#8221;. After executing **_reload udev_** then disconnecting and connecting my phone again, everything looked fine. Now I could see the name of my HTC Desire after running _**adb devices**_.
>             
>             Maybe this post helps you in setting up your Android SDK on Ubuntu. If it does please drop me a comment below.
>             
>             (Thanks to the post of <a title="it-slav.net" href="http://www.it-slav.net/blogs/2010/05/01/hint-howto-get-android-sdk-working-on-ubuntu/" target="_blank">it-slav.net</a>)
>             
>             ### Related articles {.zemanta-related-title}
>             
>             <ul class="zemanta-article-ul">
>               <li class="zemanta-article-ul-li">
>                 <a href="http://sichent.wordpress.com/2010/11/04/install-android-sdk-and-ndk/">Install Android SDK and NDK</a> (sichent.wordpress.com)
>               </li>
>               <li class="zemanta-article-ul-li">
>                 <a href="http://techblissonline.com/android-3-sdk-download/">Download Android 3.0 SDK</a> (techblissonline.com)
>               </li>
>               <li class="zemanta-article-ul-li">
>                 <a href="http://www.howtoforge.com/setting-up-an-android-app-build-environment-with-eclipse-android-sdk-phonegap-ubuntu-10.10">Setting Up An Android App Build Environment With Eclipse, Android SDK, PhoneGap (Ubuntu 10.10)</a> (howtoforge.com)
>               </li>
>               <li class="zemanta-article-ul-li">
>                 <a href="http://techblissonline.com/download-android-sdk-install-and-develop/">Download Android SDK, Install and Develop Android Apps</a> (techblissonline.com)
>               </li>
>             </ul>
>             
>             <div class="zemanta-pixie">
>               <a class="zemanta-pixie-a" title="Enhanced by Zemanta" href="http://www.zemanta.com/"><img class="zemanta-pixie-img" src="http://img.zemanta.com/zemified_e.png?x-id=ca4aa06d-094b-478c-b803-969bea0f697f" alt="Enhanced by Zemanta" /></a>
>             </div>

 [1]: http://developer.android.com/guide/developing/device.html#VendorIds