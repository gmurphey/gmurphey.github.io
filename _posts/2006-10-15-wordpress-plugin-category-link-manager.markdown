---
layout: post
title: "Wordpress Plugin: Category Link Manager"
date: 2006-10-15 00:00:00 -04:00
comments: true

github: category-links-manager
---
I can't really call this a new plugin. If you look under the hood, most of codebase is just a reworking of the popular [Page Link Manager](http://gmurphey.com/2006/10/05/wordpress-plugin-page-link-manager). It's one of the nice things about Wordpress plugin development -- being able to borrow ideas from similiar plugins -- and it's what makes scripting for Wordpress enjoyable.

The motivation behind this plugin is the fact that excluding categories is somewhat of a barrier to those of us who are not programmers. It used to be that we would have to dig through PHP templates and add `exclude=2,7` to the `wp_list_cats` tag. To clients or anyone not familiar with the Wordpress system, that may seem like an impossible task. And, for those who are comfortable with the Wordpress system, it can be just plain annoying. The Category Link Manager attempts to make things just a little bit easier.

### The Plugin

The Category Link Manager Plugin is a Wordpress plugin that adds an administration panel that allows users to pick which category links are included in the site navigation. It also provides a function that uses these settings to replace `wp_list_cats`. Adding it to your Wordpress installation is as easy as ever.

1. [Download](https://github.com/{{site.social.github}}/{{page.github}}) and unzip the plugin archive
2. Place the plugin file under wp-content/plugins directory on your Wordpress Installation
3. Log in to your admin interface and activate Category Link Manager under the 'Plugins' tab
4. Go to the new panel under the 'Manage' tab called 'Category Links'
5. Select and update the categories you want included in your site navigation
6. Open the source of the template file where you call the `wp_list_cats` function (the default file is sidebar.php, however it may be different if you're using certain plugins) and replace it with `gdm_list_selected_cats`.

If you're wondering, `gdm_list_selected_cats` is what does all the work for us. It takes the categories we chose to include in the navigation and works out what categories it should exclude. Besides that, it acts exactly like `wp_list_cats` -- it even takes [the same parameters](http://codex.wordpress.org/Template_Tags/wp_list_cats#Parameters).

Here's a few examples of what we can do:

{% highlight php %}
// sort the categories by name
gdm_list_selected_cats('sort_column=name');

// sort the list by name and show empty categories
gdm_list_selected_cats('sort_column=name&hide_empty=0');

// sort the list by name and manually exclude
// additional categories
gdm_list_selected_cats('sort_column=name&exclude=2,7');
{% endhighlight %}

Like my other Wordpress plugins, I hope to keep this plugin going as a work in progress as it helps make content management just a little bit easier. If you have any problems, questions or suggestions, please let me know.

### Requirements

The current release requires a server running at least PHP4. The plugin has been tested on Wordpress 2.x. If anyone has gotten it working on older versions of Wordpress, please let me know.
