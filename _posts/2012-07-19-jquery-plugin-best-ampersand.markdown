---
layout: post
title: "jQuery Plugin: Best Ampersand"
date: 2012-07-19
comments: true

github: jquery.best-ampersand
---
"Best Ampersand" is a simple jQuery plugin that adds ampersand classes for better ampersand fonts. Inspired by [Dan Cederholm](http://simplebits.com/notebook/2008/08/14/ampersands-2/).

### Getting Started
Download the [production version][min] or the [development version][max].

[min]: https://raw.github.com/{{site.social.github}}/{{page.github}}/master/dist/{{page.github}}.min.js
[max]: https://raw.github.com/{{site.social.github}}/{{page.github}}/master/dist/{{page.github}}.js

In your web page:

{% highlight html %}
<script src="jquery.js"></script>
<script src="dist/jquery.best-ampersand.min.js"></script>
<script>
jQuery(function($) {
  // finds and surrounds all ampersands in all <h2>s
  $('h2').bestAmpersand();
});
</script>
{% endhighlight %}

### Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [grunt](https://github.com/cowboy/grunt).

_Also, please don't edit files in the "dist" subdirectory as they are generated via grunt. You'll find source code in the "src" subdirectory!_

### Release History

- *0.1.0*: Initial release.
