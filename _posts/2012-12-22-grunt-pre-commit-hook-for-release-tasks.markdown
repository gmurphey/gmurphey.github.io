---
title: "Git Pre-Commit Hook for Grunt Release Tasks & Tests"
layout: post
date: 2012-12-22
---

I'm always forgetting to run release tasks when committing to git, and then I'm forced to either rewrite history with `rebase` or roll back and re-commit. It's a big time sink. Thankfully, I've been playing with [Grunt](http://gruntjs.com/) tasks and git pre-commit hooks and found a way to not only save time and my sanity, but take release tasks out of my manual workflow entirely. This hook will stash any work that's not staged, run the release task, stage any files created or updated by the grunt task and restore any stashed files. If you aren't using a release task, this will work equally well with `grunt jshint` or any testing tasks you may have defined.

In the pre-commit hook (`.git/hooks/pre-commit`):

{% highlight bash %}
#!/bin/sh
# stash unstaged changes, run release task, stage release updates and restore stashed files

NAME=$(git branch | grep '*' | sed 's/* //')

# don't run on rebase
if [ $NAME != '(no branch)' ]
then
  git stash -q --keep-index
  grunt release

  RETVAL=$?

  if [ $RETVAL -ne 0 ]
  then
    exit 1
  fi

  git add .
  git stash pop -q
fi
{% endhighlight %}

And in your Grunt config:

{% highlight javascript %}
grunt.registerTask('release', ['lint', 'qunit', 'concat', 'min']);
{% endhighlight %}

Never commit linting errors or failing tests again, and let git save your sanity with automated grunt tasks.
