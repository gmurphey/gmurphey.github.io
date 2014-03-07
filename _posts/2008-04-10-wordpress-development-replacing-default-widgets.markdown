---
layout: post
title: "WordPress Development: Replacing Default Widgets"
date: 2008-04-10
comments: true
---
I've been working on a little WordPress project these last few weeks with a colleague. When I first heard the idea, I thought, "That should be easy enough to build." I decided the best way to tackle the feature would be a custom widget, but when I finally sat down to get it working I quickly began to realize that there were a few obstacles to overcome.

The project was really meant to extend an existing widget, and it seemed confusing to have both the default and extended version there side by side (plus it would be really nice to call them the same thing for transparency). I needed to get rid of it. You can't just overwrite an existing widget by registering a new one by the same name - WordPress ignores it. And if I did manage to find a way to remove a default widget, when do you have to do it?

Luckily, some digging around found a solution.

{% highlight php %}
function gdm_widget_meta_register() {
 // unregister the widget and its control
 wp_unregister_sidebar_widget('meta');

 // register the new and improved widget and control
 wp_register_sidebar_widget('meta', __('Meta'), 'gdm_widget_meta');
 wp_register_widget_control('meta', __('Meta'), 'gdm_widget_meta_control');
}

add_action('widgets_init', 'gdm_widget_meta_register', 1);
{% endhighlight %}

The really important pieces are the `wp_unregister_sidebar_widget` function and the `widgets_init` action hook. `widgets_init` actions are run right after all the default widgets are registered, giving us the perfect opportunity to call `wp_unregister_sidebar_widget` with the ID of the widget you're getting rid of. Now you can register your own widget and control, effectively replacing a default WordPress widget.
