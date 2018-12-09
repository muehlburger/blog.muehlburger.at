+++
author = "Herbert Mühlburger"
bitcointips_address = ["1DXXtP327gENAHaH7pMA1VpWk4Y9bFNU4y"]
categories = ["Uncategorized"]
date = "-001-11-30T00:00:00+00:00"
draft = true
tags = ["Git", "Qualität"]
title = "5 Nützliche Tips für eine bessere Commit Message"
type = "post"
url = "/?p=1783"

+++
Jeder, der mit einem Quellcode-Versionierungssystem wie <a title="Git" href="http://git-scm.com/" target="_blank">Git</a> arbeitet, sollte sich die folgenden fünf Tips zu Herzen nehmen um die Commit Messages zu verbessern. Durch bessere Commit Messages wird auch die Dokumentation des Projekts implizit verbessert. Frei nach dem Motto: &#8220;Der Code ist die beste Dokumentation&#8221; hier nun die fünf Tips:

  * Die erste Zeile sollte sollte nicht mehr als 50 Zeichen beinhalten.
  * Überprüfe die Rechtschreibung und Grammatik der Commit Message zweimal.
  * Vermeide das -m / &#8211;message= Flag bei git commit.

Eine verbesserte Commit Message sieht in etwa wie folgt aus:

[sourcecode language=&#8221;bash&#8221;]
  
Redirect user to the requested page after login</pre>
  
https://trello.com/path/to/relevant/card
  
<pre>
  
Users were being redirected to the home page after login, which is less
  
useful than redirecting to the page they had originally requested before
  
being redirected to the login form.

* Store requested path in a session variable
  
* Redirect to the stored location after successfully logging in the user
  
[/sourcecode]

(via <a title="robots.thoughtbot.com" href="http://robots.thoughtbot.com/post/48933156625/5-useful-tips-for-a-better-commit-message" target="_blank">robots.thoughtbot.com</a>)