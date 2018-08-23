---
title: What means Serverless?
author: Herbert Mühlburger
type: post
date: 2018-01-29T15:34:05+00:00
url: /2018/01/what-are-serverless-architectures/
categories:
  - Serverless
  - Technology
tags:
  - BaaS
  - FaaS
  - PaaS
  - Serverless

---
For those who want to understand &#8220;Serverless architectures&#8221;, I recommend reading <a href="https://martinfowler.com/articles/serverless.html" target="_blank" rel="noopener">this post</a> by <a href="https://twitter.com/mikebroberts" target="_blank" rel="noopener">Mike Roberts</a>. The term Serverless was already used <a href="https://readwrite.com/2012/10/15/why-the-future-of-software-and-apps-is-serverless/" target="_blank" rel="noopener">in 2012</a>. Mike defines the following characteristics of serverless architectures:

### Mike Roberts&#8217; Definition of Serverless

#### No management of server hosts or server processes

You as a developer don&#8217;t have to care about e.g. the number of servers running your software or where where it runs or things like OS upgrades, etc.

#### Self auto-scale and auto-provision based on load

#### Costs based on precise usage

<div id="text-3-71-1-3" class="outline-text-5">
  <p>
    Get charged based on usage. Don&#8217;t get charged if you don&#8217;t use a service. Platform itself should auto-scale or spin up new things and also terminate them according to the current need without having anybody involved.
  </p>
</div>

#### Performance capabilities defined in terms other than host size/count

<div id="text-3-71-1-4" class="outline-text-5">
  <p>
    Serverless gives you higher level of abstraction which also means that you loose some of the control of lower levels.
  </p>
</div>

#### Implicit high availability

<div id="text-3-71-1-5" class="outline-text-5">
  <p>
    You don&#8217;t have to apply concious thought, you get high availabilty as a side effect of using the serverless product.
  </p>
  
  <p>
    Recently Sam Newman, the author of the book &#8220;<a href="https://samnewman.io/books/building_microservices/">Building Microservices</a>&#8220;, gave a good <a href="https://www.youtube.com/watch?v%253DaZlrv-0PE_c">talk</a> on the same topic and here is the video.
  </p>
  
  <p>
  </p>
</div>

Serverless is all about abstracting away things in certain levels. Kelsey Hightower&#8217;s tweet makes an interesting point:

<blockquote class="twitter-tweet" data-width="550" data-dnt="true">
  <p lang="en" dir="ltr">
    I now understand what all the Serverless fuss is about. When you have a great idea the last thing you want to do is setup infrastructure.
  </p>
  
  <p>
    &mdash; Kelsey Hightower (@kelseyhightower) <a href="https://twitter.com/kelseyhightower/status/856272003963039744?ref_src=twsrc%5Etfw">April 23, 2017</a>
  </p>
</blockquote>



I hope you found some interesting links in this article and if you did, post additional material or share this one.

(via [GOTO 2017][1])

 [1]: https://www.youtube.com/watch?v=aZlrv-0PE_c