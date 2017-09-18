---
title: Increase Jekyll Build Speed
desc: Jekyll build speed slows down with the increase in the number of files, posts, images etc.. Jekyll community is trying hard to mitigate the high build time. I will be discussing a few methods on how to increase jekyll build speed.
author: sharathdt
tags: Jekyll
image: jekyll-build-speed.png
layout: post
permalink: /jekyll-build-speed/
---

Jekyll build speed is an important aspect in my blog because, after publishing some 20 articles, Jekyll used to take around 30 seconds to build this website! That is more than what it takes to make an omelette. Build time started to grow gradually as and when I started adding new features and I got really fed up once it reached 8 minutes!

Jekyll is super fast when it comes to sites with a few pages. It tends to slow down when the number of files increases and when complex Liquid conditions are executed frequently. The files usually cause this delay are posts, images, collections etc..

* Do not remove this line (it will not be displayed) 
{:toc}


Jekyll is trying hard to decrease the build time since the inception. One of those measures was using incremental build. In **incremental build**, Jekyll watches only for the files which are changed, not everything. This works well if a site is simple. Imagine you change something on the ``default.html`` layout, then the build time again increases because that layout is used for every single post and every single page.

{% include adsense-inside-post.html %}

Before we jump right into the methods, let's discuss some precautions that may reduce the build time drastically.

## Exclude files that are not required
I see that some people use task runners like grunt, gulp or others which make use of ``node-modules``. Node will create a folder in the repository with the same name and this folder is a mess. I think the movie Inception was simpler than this folder nest.

This folder is important for task-runners but not required for Jekyll to build the site. So exclude anything that isn't important. Use ``exclude`` in ``_config.yml``.

{% highlight yml %}
exclude: [node_modules, README.md]
{% endhighlight %}


## Keep_files that are required as-is
Your site maybe using some static files and they should be copied as-is while building the site. For example ``images`` folder. Jekyll has nothing to do with those images. Static files that do not need any Jekyll intervention can be kept as-is using these parameters in the configuration.


{% highlight yml %}
keep_files: [images]
{% endhighlight %}

## Test Jekyll Build Speed


Now that we have retained only the required files for Jekyll to render, we should check if there is a slowdown in the speed while Jekyll is performing the conversion.

If you have too many nested liquid tags then the build time will increase drastically. Jekyll slows down while building if you are using too many includes.

What I suggest is to reduce the usage of **includes**. If any included file has a liquid condition, then the jekyll build speed increases.

Consider my website for example. I have too many files inside ``_includes``(but not using all of them) and I also use ``compress html``. This is a layout used to minify HTML. It has too many liquid tags in it. This takes a considerable amount of time (around a second) for the completion.

Run below Liquid Profiler command to check which liquid syntax execution is taking too much time.

{% highlight yml %}
jekyll serve --profile
{% endhighlight %}

{% include adsense-inside-post-2.html %}

It should output a table as shown below. This will give you a fair idea on what might be going wrong. If a file is taking too many seconds to execute then you should try to carefully examine that file for any nesting of liquid syntax.

{% highlight yml %}

Filename                                       | Count |    Bytes |  Time
---------------------------------------------- +-------+----------+------

_posts/2016-05-27-jekyll-collections.md        |     1 |   13.63K | 0.008
_posts/2016-07-21-better-related-posts.md      |     1 |   13.70K | 0.008
_posts/2017-03-15-speed-up-jekyll-build.md     |     1 |    7.28K | 0.007
_posts/2016-01-20-how-to-add-share-buttons-to- |     1 |   13.02K | 0.007
_posts/2016-11-12-dark-theme-switch.md         |     1 |   11.99K | 0.007
_posts/2016-04-27-jekyll-speed.md              |     1 |   28.40K | 0.007
_posts/2016-07-18-jekyll-search.md             |     1 |   11.81K | 0.006
_pages/jekyll-themes.md                        |     1 |    8.12K | 0.006
_posts/2016-08-10-common-jekyll-issues.md      |     1 |   12.83K | 0.006
_includes/google-tag-manager-head.html         |    75 |   31.49K | 0.006
_posts/2016-12-20-jekyll-liquid-common-tags.md |     1 |   12.84K | 0.005
_posts/2016-01-25-an-easy-way-to-edit-posts-in |     1 |    7.48K | 0.005
_posts/2016-08-30-jekyll-admin.md              |     1 |    6.92K | 0.005

{% endhighlight %}

## Use Jekyll incremental build
Building the site from the scratch everytime is not practical. This is why Jekyll provides an option for an incremental build which converts only the files that are changed. This way the jekyll build speed can be increased in multiple folds.

[Incremental build](https://jekyllrb.com/news/2015/10/26/jekyll-3-0-released/)

The initial release of the incremental build was not so efficient, but recent releases work fairly good. Jekyll is making a lot of improvements. Maybe some day it can compete with the build speeds of Hugo(very optimistic!)

Use the command below for incremental build

{% highlight yml %}
jekyll serve -I
{% endhighlight %}

or

{% highlight yml %}
jekyll serve --incremental
{% endhighlight %}


Compare the incremental build speed with normal build speed check if it has improved anything. Many times, I had no luck with this method. If none of that works then follow the last method.

## Let Jekyll build only the necessary posts
If your site has too many articles, you may find this method very useful. Some people with 100s of posts have a hard time building their Jekyll site locally. In those situations, you can build only the last post! This can be used even while editing the site layout or pages.


{% highlight yml %}
jekyll serve --watch --limit_posts 1
{% endhighlight %}


## Conclusion
When compared to Hugo or Gatsby, Jekyll build speed is really slow. But it is changing. Jekyll is making leaps in decreasing build time. Until then I hope these hotfixes will help you stick to Jekyll and not switch to other platforms.

If you have a better way to increase jekyll build speed, then please suggest it in the comment section. Also, watch this video of Parker explaining the new features in Jekyll 3.4, Incremental build, Liquid Profiler etc..

<iframe class="video" src="https://www.youtube.com/embed/sPZK8w55cBQ?rel=0" frameborder="0" allowfullscreen></iframe>