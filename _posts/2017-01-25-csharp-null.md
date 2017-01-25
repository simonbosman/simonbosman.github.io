---
layout: default
title:  "Checking for NPE(Null Pointer Exception) got a whole lot less onerous."
date:   2017-01-25 15:21:00
categories: main
---

When programming you will have to perform numerous NPE checks, in C# 6.0 Microsoft introduced monadic null checking.
Although this is already some time available, I just found out.<br><br>
So instead of doing this:

{% highlight csharp %}

if (points != null) {
  var next = points.FirstOrDefault();
  if (next != null && next.X !=null) {
    return next.X;
  }
}
return -1

{% endhighlight %}

You can do this:

{% highlight charp %}

return points?.FirstOrDefault()?.X ?? -1;

{% endhighlight %}

After some time you are really starting to like it.
