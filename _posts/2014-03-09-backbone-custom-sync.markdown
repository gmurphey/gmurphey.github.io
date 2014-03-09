---
title: "Backbone.CustomSync"
layout: post
date: 2014-03-09

github: backbone.customsync
---

Many times while building a [Backbone.js](http://backbonejs.org) application, you'll either be working with an API wrapped by a library or non-RESTful resources. This can be a pain, and you'll most likely end up having to override `Backbone.sync` with a [giant `switch` statement](http://dailyjs.com/2012/12/20/backbone-tutorial-4/). If you're writing tests against this new `sync` method, it can seem near impossible to cover all the cases. Backbone.CustomSync attempts to alleviate some of that pain by extending `Backbone.sync` to allow for custom behavior for each of the `sync` procedures.

### Getting Started

Backbone.CustomSync is available via both NPM and Bower. To install:

{% highlight bash %}
## npm
npm install -s backbone.customsync

## bower
bower install -S backbone.customsync
{% endhighlight %}

Backbone.CustomSync is [AMD](http://requirejs.org/) and CommonJS ready.

To use the extension, all you have to do is use `Backbone.CustomSync.Model` or `Backbone.CustomSync.Collection` in place of `Backbone.Model` and `Backbone.Collection`, respectively. For example.

{% highlight javascript %}
var Model = Backbone.CustomSync.Model.extend({
  readSync: function (options) {
    if (successful) {
      options.sucess(this, response, options);
    } else {
      options.error(this, response, options);
    }
  },

  createSync: function (options) {
    if (successful) {
      options.success(this, response, options);
    } else {
      options.error(this, response, options);
    }
  },

  updateSync: function (options) {
    if (successful) {
      options.success(this, response, options);
    } else {
      options.error(this, response, options);
    }
  }, 

  deleteSync: function (options) {
    if (successful) {
      options.success(this, response, options);
    } else {
      options.error(this, response, options);
    }
  }
});
{% endhighlight %}

If you don't define one of these sync methods -- `createSync`, for example -- and Backbone attempts to save a new model, the `options.error` callback will be invoked automatically. **Backbone.CustomSync will only perform the operations you define**.

If, for some reason, you want to use the default `Backbone.sync` functionality for one of your sync procedures, that's easy.

{% highlight javascript %}
var Model = Backbone.CustomSync.Model.extend({
  readSync: function (options) {
    this.xhrSync('read', this, options);
  }
});
{% endhighlight %}

Hopefully Backbone.CustomSync can make working on models and collections with unconventional Backbone resources easier and more enjoyable. As always, feel free to file an issue or file a pull request. Enjoy!
