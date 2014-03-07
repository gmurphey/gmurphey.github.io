---
layout: post
title: "jQuery Plugin: Outbound Analytics"
date: 2012-07-22
comments: true

github: jquery.outbound-analytics
---
A jQuery plugin aimed at making it easier to track outbound (external) links with Google Analytics.

### Getting Started
Download the [production version][min] or the [development version][max].

[min]: https://raw.github.com/{{site.social.github}}/{{page.github}}/master/dist/{{page.github}}.min.js
[max]: https://raw.github.com/{{site.social.github}}/{{page.github}}/master/dist/{{page.github}}.js

99% of the time you'll probably just want to track clicks on all outbound links on a page. This is easy. In your web page:

{% highlight html %}
<script src="jquery.js"></script>
<script src="dist/jquery.outbound-analytics.min.js"></script>
<script>
jQuery(function($) {
  // automatically tracks all outbound links (a[href]) in the DOM
  $.outboundAnalytics();
});
</script>
{% endhighlight %}

Sometimes you may want to track only certain links, or track links in your header or footer different. This is easy, too. In your web page:

{% highlight html %}
<script src="jquery.js"></script>
<script src="dist/jquery.outbound-analytics.min.js"></script>
<script>
jQuery(function($) {
  // automatically tracks all outbound links (a[href]) in <header>
  $('header').outboundAnalytics();

  // track <aside> links as 'Reference Links'
  $('aside').outboundAnalytics({ 'category': 'Reference Links' });
});
</script>
{% endhighlight %}

### Fully Customizable
The plugin comes with smart defaults and [everything you pass to Google Analytics](https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide#Anatomy) is totally customizable (options can even be passed as functions). Here's what you have access to:

| Name           | Type    | Default                   | Description                                                                  |
| -------------- | ------- | ------------------------- | ---------------------------------------------------------------------------- |
| category       | String  | Outbound Links            | The category used in Google Analytics                                        |
| action         | String  | Click                     | The action used in Google Analytics                                          |
| label          | String  | The link's href attribute | The label used in Google Analytics                                           |
| value          | Float   | null                      | The value assigned to the event in Google Analytics                          |
| nonInteraction | Boolean | false                     | Whether or not the event calculates into the bounce rate in Google Analytics |

### Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [grunt](https://github.com/gruntjs/grunt).

_Also, please don't edit files in the "dist" subdirectory as they are generated via grunt. You'll find source code in the "src" subdirectory!_

### Release History

- *0.1.1*: Improving external link detection.
- *0.1.0*: Intial release.
