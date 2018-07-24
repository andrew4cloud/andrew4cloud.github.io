---
layout: post
title:  "Changing a remote's URL"
date:   2018-07-23 15:55:51 +0530
categories: version control
---

In this post you will find how to change a remote url & how to switch between remote URLs from SSH to HTTPS & Switching remote URLs from HTTPS to SSH

Lets Get started!!!

The git remote set-url command changes an existing remote repository URL.

The git remote set-url command takes two arguments:

An existing remote name. For example, origin or upstream are two common choices.
A new URL for the remote. For example:

If you're updating to use HTTPS, your URL might look like:

{% highlight ruby %}
https://github.com/USERNAME/REPOSITORY.git
{% endhighlight %}

If you're updating to use SSH, your URL might look like:

{% highlight ruby %}
git@github.com:USERNAME/REPOSITORY.git
{% endhighlight %}

## Switching remote URLs from SSH to HTTPS

Step-1 : Open Terminal

Step-2 : Change the current working directory to your local project.

Step-3 : List your existing remotes in order to get the name of the remote you want to change.


{% highlight ruby %}
git remote -v
origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
origin  git@github.com:USERNAME/REPOSITORY.git (push)
{% endhighlight %}

Step-4 : Change your remote's URL from SSH to HTTPS with the git remote set-url command.

{% highlight ruby %}
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
{% endhighlight %}

Step-5 : Verify that the remote URL has changed.

{% highlight ruby %}
git remote -v
# Verify new remote URL
origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
origin  https://github.com/USERNAME/REPOSITORY.git (push)
{% endhighlight %}

The next time you git fetch, git pull, or git push to the remote repository, you'll be asked for your GitHub username and password.

--> If you have two-factor authentication enabled, you must create a personal access token to use instead of your GitHub password.

--> You can use a credential helper so Git will remember your GitHub username and password every time it talks to GitHub.

## Switching remote URLs from HTTPS to SSH

Step-1 : Open Terminal.

Step-2 : Change the current working directory to your local project.

Step-3 : List your existing remotes in order to get the name of the remote you want to change.

{% highlight ruby %}
git remote -v
origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
origin  https://github.com/USERNAME/REPOSITORY.git (push)
{% endhighlight %}

Step-4 : Change your remote's URL from HTTPS to SSH with the git remote set-url command.

{% highlight ruby %}
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
{% endhighlight %}

Step-5 : Verify that the remote URL has changed.

{% highlight ruby %}
git remote -v
# Verify new remote URL
origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
origin  git@github.com:USERNAME/REPOSITORY.git (push)
{% endhighlight %}

## Troubleshooting

You may encounter these errors when trying to changing a remote.

### No such remote '[name]'

This error means that the remote you tried to change doesn't exist:

{% highlight ruby %}
git remote set-url sofake https://github.com/octocat/Spoon-Knife
fatal: No such remote 'sofake'
{% endhighlight %}

Check that you've correctly typed the remote name.
