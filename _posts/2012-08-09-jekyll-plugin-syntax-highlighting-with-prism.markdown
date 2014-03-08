---
title: "Jekyll: Replacing Pygments Highlighting With Prism.js"
layout: post
date: 2012-08-09

github: jekyll-prism-plugin
---

I've been battling with Pygments, the native [Jekyll](https://github.com/mojombo/jekyll/) markup highlighter, for a while. Its reliance on Python makes it nearly impossible to run on Heroku without committing your compiled site to git (which just makes me feel dirty). Needless to say, I've been looking for a Pygments alternative for a while. That's why I was excited to see [Lea Verou](http://lea.verou.me/) announce [Prism](http://prismjs.com/), a standalone and lightweight client-side syntax highlighter.

### The Setup

The Prism plugin is very easy to install and start using.

Simply [download the plugin](http://github.com/{{site.social.github}}/{{page.github}}), copy `prism.rb` to your plugins folder setup your layout to use the [Prism JavaScript and styles](http://prismjs.com/download.html).

{% highlight html %}
<html>
  <head>
    <link href="prism.css" rel="stylesheet" type="text/css">
  </head>
  <body>
    ...
    <!-- after all your content -->
    <script src="prism.js"></script>
  </body>
</html>
{% endhighlight %}

### Getting Started

Much of my work on the plugin is based on the Jekyll's native `highlight` tag, and it's used much the same way.

For a plain, old vanilla experience (like you see on this page), the syntax is pretty straightforward.

{% highlight html %}
... content ...
{% raw %}
{% prism javascript %}
var obj = { 'foo': true, 'bar': false };

for (key in obj) {
  console.log(obj[key]);
}
{% endprism %}
{% endraw %}
... more content ...
{% endhighlight %}

Like Jekyll's `highlight`, the Prism plugin also can highlight lines using `linenos`. The value can be a comma-separated list or a range (1, 3-7).

*Note:* you need to include line highlighting in your Prism download for this to work.

{% highlight html %}
... content ...
{% raw %}
{% prism javascript linenos=1,4 %}
var obj = { 'foo': true, 'bar': false };

for (key in obj) {
  console.log(obj[key]);
}
{% endprism %}
{% endraw %}
... more content ...
{% endhighlight %}

And for something Prism doesn't offer out of the box, declaring `linenos` without a value will highlight all lines.

{% highlight html %}
... content ...
{% raw %}
{% prism javascript linenos %}
var obj = { 'foo': true, 'bar': false };

for (key in obj) {
  console.log(obj[key]);
}
{% endprism %}
{% endraw %}
... more content ...
{% endhighlight %}

### Fork it!

As usual, all the code for the plugin is [hosted on GitHub](http://github.com/{{site.social.github}}/{{page.github}}). If you find a bug, please file an issue or request a pull.
