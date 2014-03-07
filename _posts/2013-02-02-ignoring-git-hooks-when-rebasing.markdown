---
title: "Ignoring Git Hooks When Rebasing"
layout: post
date: 2013-02-02
---

If you're in the habit of running `git rebase` before pushing to origin (and you should be, in my opinion), you may notice some annoying things happening if you have `prepare-commit-msg` and `pre-commit` hooks enabled for your repository. I have both -- one to pre-prend the branch name on my commit messages and [another to run build processes](/2012/12/22/grunt-pre-commit-hook-for-release-tasks.html). When I would clean up my commits with an interactive rebase each of the commits in the rebase would have their messages edited and a build would be made for every step of the way. That finally annoyed me enough to add a simple condition to my hooks.

{% highlight bash %}
#!/bin/sh
BRANCH_NAME=$(git branch | grep '*' | sed 's/* //')

if [ $BRANCH_NAME != '(no branch)' ]
then
  # your regularly scheduled hook
fi
{% endhighlight %}

Now those commits won't run when rebasing (rebase runs in a headless branch) and you could technically run a separate hook just for rebases.
