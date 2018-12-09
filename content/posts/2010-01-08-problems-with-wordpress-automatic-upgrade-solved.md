+++
aktt_notify_twitter = ["yes"]
aktt_tweeted = ["1"]
author = "Herbert Mühlburger"
bitcointips_address = ["17jewy7eKRSas6gPJMGo45USKVhx5YspgQ"]
categories = ["Computer Science"]
date = "2010-01-08T16:32:13+00:00"
dsq_thread_id = ["250190751"]
tags = ["Blog", "Failure", "google", "weblog", "Website", "wordpress"]
title = "Problems with WordPress Automatic Upgrade solved"
type = "post"
url = "/2010/01/problems-with-wordpress-automatic-upgrade-solved/"

+++
<div class="zemanta-img">
  <div>
    <dl class="wp-caption alignright">
      <dt class="wp-caption-dt">
        <a href="http://www.crunchbase.com/product/wordpress"><img title="Image representing WordPress as depicted in Cr..." src="http://www.crunchbase.com/assets/images/resized/0001/6548/16548v2-max-250x250.png" alt="Image representing WordPress as depicted in Cr..." /></a>
      </dt>
      
      <dd class="wp-caption-dd zemanta-img-attribution">
        Image via <a href="http://www.crunchbase.com">CrunchBase</a>
      </dd>
    </dl>
  </div>
</div>

While trying to upgrade my <a title="Wordpress" href="http://www.wordpress.org" target="_blank">WordPress</a> installation from version 2.9 to version 2.9.1 I always got the following error:

> _Downloading update from http://wordpress.org/wordpress-2.9.1.zip._
  
> Download failed.: Operation timed out with 1201840 out of -1 bytes received
  
> Installation Failed

After doing some research using <a title="Google" href="http://www.google.com" target="_blank">Google </a>I found a solution to that problem:

You just need to edit the following file in order to increase the download timeout:

<pre class="brush: php">/wp-admin/includes/file.php</pre>

Near line 461 of file.php change the timeout value from:

<pre class="brush: php">$response = wp_remote_get($url, array('timeout' =&gt; 60));</pre>

to the new value of 120:

<pre class="brush: php">$response = wp_remote_get($url, array('timeout' =&gt; 120));</pre>

Then try again to upgrade your wordpress installation using the automatic upgrade and it should work properly now. Mine did and I am happy again! 🙂

Cheers and have fun, and leave me a comment if this post was useful for you!

Herbert

###### Related articles by Zemanta {.zemanta-related-title}

<ul class="zemanta-article-ul">
  <li class="zemanta-article-ul-li">
    13 WordPress Plug-in & Hacks for powering your Blogging Experience (franklinbishop.net)
  </li>
  <li class="zemanta-article-ul-li">
    <a href="http://www.makeuseof.com/tag/wordpress-exploit-scanner-helps-administrators-scan-their-database-for-malicious-files/">WordPress Exploit Scanner Helps Administrators Scan Their Database For Malicious Files</a> (makeuseof.com)
  </li>
</ul>

<div class="zemanta-pixie">
  <a class="zemanta-pixie-a" title="Reblog this post [with Zemanta]" href="http://reblog.zemanta.com/zemified/b43f9d31-c9ac-44bc-b735-45429630585f/"><img class="zemanta-pixie-img" src="http://img.zemanta.com/reblog_e.png?x-id=b43f9d31-c9ac-44bc-b735-45429630585f" alt="Reblog this post [with Zemanta]" /></a><span class="zem-script more-related pretty-attribution"></span>
</div>