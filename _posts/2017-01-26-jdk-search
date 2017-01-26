---
layout: default
title:  "Search for Java documentation"
date:   2017-01-26 10.03
categories: main
---

When searching for Java documentation the [first search results](https://github.com/simonbosman/simonbosman.github.io/blob/master/content/Java7SearchResult.PNG)
will redirect you to the Java Platform SE 7 documentation.<b>
This userscript will automatically redirect you to the [Java Platform SE 8 documentation](https://github.com/simonbosman/simonbosman.github.io/blob/master/content/Java8SearchResult.PNG) <br>
Thanks [Yawkat](http://yawk.at/) for the userscript.

{% highlight javascript %}
// ==UserScript==
// @name        JDK 8 docs
// @namespace   at.yawk.jdk8docs
// @include     https://docs.oracle.com/javase/*
// @version     1
// @grant       none
// ==/UserScript==

var pattern = /^(https?:\/\/docs\.oracle\.com\/javase\/)(?:7|6|1\.5\.0)(\/.*)$/i;
var result = pattern.exec(window.location.href);
if (result) {
  window.location = result[1] + "8" + result[2];
}
{% endhighlight%}
