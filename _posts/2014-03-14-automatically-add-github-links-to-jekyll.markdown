---
title: "Automatically Add GitHub Links to Jekyll Posts"
layout: post
date: 2014-03-14
---

When I switched to Jekyll, one of the first features I embraced was the Liquid syntax. Markdown is a joy to write, and having a template abstraction layer like Liquid makes templating equally easy and understandable. Using yaml abstracts that templating logic even further. Being an open source contributor, I wanted a maintainable way write about and link to projects I was working on.

To start, I added some site-wide settings. Appended to `_.config.yml`:

{% highlight yaml %}
social:
  github: gmurphey
  twitter: gmurphey
{% endhighlight %}

And then in each post that was about a GitHub project, I added the `github` setting pointing to the repository name.

{% highlight html %}
{% raw %}
---
title: "Github test"
layout: post
date: 2014-03-11

github: github-test
---
{% endraw %}
{% endhighlight %}

And then finally, I hooked the two up in the my post layout:

{% highlight html %}
{% raw %}
{% if site.social.github and page.github %}
<ul>
  <li>
    <a href="http://github.com/{{site.social.github}}/{{page.github}}">
      View on GitHub
    </a>
  </li>
</ul>
{% endif %}
{% endraw %}
{% endhighlight %}

I also add links to download, fork, and file an issue on GitHub. Writing about and pointing readers to projects I'm working on is now maintainable and conveninent.
