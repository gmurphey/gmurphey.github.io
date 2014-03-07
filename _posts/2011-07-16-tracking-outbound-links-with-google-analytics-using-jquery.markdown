---
layout: post
title: Tracking Outbound Links with Google Analytics and jQuery
date: 2011-07-16
comments: true
---
Here's a quick event binding I wrote today for the site to track outbound links in Google Analytics using some jQuery selector trickery.

### Update

I've been using this a lot, and, rather than copying and pasting it repeatedly, I decided to develop it into a real and true jQuery plugin. [Download it](http://github.com/gmurphey/jquery.outbound-analytics) and fork away!

{% highlight javascript %}
(function ($) {
  $(function () {
    $('a[href^="http:"]:not(a[href^="http://' + document.location.hostname + '"])').click(function () {
      try { _gat._getTrackerByName()._trackEvent('Outbound Links', $(this).attr('href')); } catch (e) {}
    });
  });
}) (jQuery);
{% endhighlight %}

### What's going on here?

The selector's doing most of the work here - looking for anchors linking to absolute URLs, and then basically filtering out anchors with absolute URLs pointing to the current document's domain. When the outgoing links are clicked, we fire off the [event tracking](http://code.google.com/apis/analytics/docs/tracking/eventTrackerGuide.html) method in Google Analytics. This clicks will be categorized as "Outbound Links" and the anchor's full URL will be tracked as an Action.
