---
layout: post
title: "WordPress Plugin: Page Link Manager"
date: 2006-10-05
comments: true
---
WordPress is a fantastic tool -- I can't say that enough. I was able to migrate my old site and structure over to the WordPress model quite quickly, and in a matter of minutes I was blogging. But one of the major hurdles is that it still relies on coding knowledge a bit. For example, under the current version of WordPress, to exclude a pages from site navigation, you have to go into the source and do something like `wp_list_pages('exclude=3,7')`. And, if you add other pages you don't want listed in the site navigation, you have to go into and edit the source each time. This became an obstacle recently when my sister and I began looking at WordPress as a viable content management system for clients' use. It seemed silly to us that each time the client wanted to include an excluded page or exclude a new page they'd have to call on us, or we'd have to teach them some elementary programming skills. And so the Page Link Manager Plugin was created.

### The Plugin

The Page Link Manager Plugin (I know it's a mouthful) is a WordPress plugin that adds an administration panel that allows users to pick which page links are included in the site navigation. Adding it to your WordPress installation is as easy as ever.

1. [Download](http://downloads.wordpress.org/plugin/page-link-manager.zip) and unzip the plugin archive
2. Place the plugin file under wp-content/plugins directory on your Wordpress Installation
3. Log in to your admin interface and activate Page Link Manager under the 'Plugins' tab
4. Go to the new panel under the 'Tools' tab called 'Page Links'. If you use widgets, you can access page link settings through the Page widget
5. Select and update the pages you want included in your site navigation.

Here's a few uses of the `wp_list_pages` function:

{% highlight php %}
// add a heading to the page link list
wp_list_pages('title_li=<h2>Pages</h2>');

// sort list by the menu order
wp_list_pages('title_li=&sort_column=menu_order');

// add a heading to the page link list and
// exclude a couple extra pages
wp_list_pages('title_li=<h2>Pages</h2>&exclude=4,7');
{% endhighlight %}

Take a look at that last example again. Can we just manually exclude pages that way even if the function's loading pre-defined excluded pages? Of course we can. The function's designed to look for and deal with manual page exclusions.

I hope to keep this plugin going as a work in progress as it helps make content management just a little bit easier. If you have any problems, questions or suggestions, please let me know.

### Requirements

The current release requires a server running at least PHP4. The plugin has been tested on Wordpress 2.5+. If anyone has gotten it working on older versions of WordPress, please let me know.

### Resources

If you're interested in writing plugins, the [WordPress plugin tutorial](http://codex.wordpress.org/Writing_a_Plugin) is an excellent resource.
