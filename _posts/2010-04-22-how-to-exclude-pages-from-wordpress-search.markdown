---
layout: post
title: How to Exclude Pages from WordPress' Search
date: 2010-04-22
comments: true
---
While working on the new theme for the site, I quickly realized that I didn't want to show pages in any of the searches on the site. I only wanted posts.

It was easy enough to find articles that illustrated ways to exclude certain categories or posts by ID, so I decided to apply those methods to pages as well. Simply paste the following into your theme's `functions.php` file.

{% highlight php %}
function gdmExcludePagesInSearch($query) {
 if ($query->is_search) {
  $query->query_vars['post__not_in'] = get_all_page_ids();
 }

 return $query;
}

add_filter('pre_get_posts', 'gdmExcludePagesInSearch');
{% endhighlight %}

This will remove all pages from [the loop](http://codex.wordpress.org/The_Loop), and only on the search page.

Something unclear, or have something to add? Please leave a comment.
