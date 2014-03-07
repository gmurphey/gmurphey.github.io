---
layout: post
title: "WordPress Plugin: Home Page Link"
date: 2007-07-31
comments: true
---
I received an email this evening from Dan, who uses the [Page Link Manager](http://gmurphey.com/2006/10/05/wordpress-plugin-page-link-manager), wondering how to get a home page link to show up in his site navigation. I had never really thought about the problem, or even realized it was a problem until I started my search for a solution. There's not much out there covering the issue besides a few forum posts at WordPress.org. But [it's a problem](http://lorelle.wordpress.com/2007/03/22/dont-get-rid-of-your-home-link-how-to-add-a-home-link/), nevertheless. I understand that the blog's heading is supposed to link to your home page, but I believe there's a large audience of Internet users, and potential readers, that wouldn't think to look to a heading for a shortcut back to your home page.

And so we have the Home Page Link plugin.

### The Plugin

The plugin does just what you think - adds a Home link to your site navigation (`wp_list_pages`). And it's very easy to use.

1. [Download](/projects/wp/home_page_link/home-page-link-v015.zip) and unzip the plugin archive
2. Place the plugin file under wp-content/plugins directory on your Wordpress Installation
3. Log in to your admin interface and activate Home Page Link under the 'Plugins' tab

That's it! You should now be able to view your site with its shiny new Home link.

Like my other plugins, I hope to keep this going as a work in progress, and work along with the WordPress community to make it more useful and efficient. If you have something you'd like to see in an upcoming version, please don't hesitate to add a comment or [contact me](/contact).

### Requirements

The current release requires a server running at least PHP4. The plugin has been tested on Wordpress 2.x. If anyone has gotten it working on older versions of Wordpress, please let me know.

### Resources

If you're interested in writing plugins, the [WordPress plugin tutorial](http://codex.wordpress.org/Writing_a_Plugin) is an excellent resource.
