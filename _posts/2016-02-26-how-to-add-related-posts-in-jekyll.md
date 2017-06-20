---
title: How to Add Related or Previous Next Pagination in Jekyll?
desc: Giving a link to next and previous posts at the bottom of the article helps to keep your users hooked to checkout more content on your website. If they like your current article, then there is a good chance that they would like to browse more articles.
keywords: add related post jekyll, jekyll related post, next previous post jekyll
author: sharathdt
tags: Jekyll
image: adding-related-previous-next-link-to-jekyll.png
layout: post
redirect_from: 
    - how-to-add-related-posts-in-jekyll/
permalink: /related-post-jekyll/
---


A long time ago I was writing 4 posts on WordPress installation tutorial. At the end of every article, I had to leave the next or previous article link. I used to do it manually in this way "To read my previous article on WordPress basics read [part 1](#)" and "for useful WordPress plugins read [part 3](#)" 



* Do not remove this line (it will not be displayed) 
{:toc}


Manually linking articles was a tedious job if I had more articles. May be there was a plugin for that, but I was fed up with too many plugins! In Jekyll, it is wasy to implement navigation because we have nice little variables ```page.previous```and ```page.next``` which can handle navigation without breaking a sweat.

{: .clear}

## Why use Related Prev-Next Navigation in Jekyll?

Finding content on your blog should be easy. Let's say a new visitor is checking out an article on your website about **How to begin with Angular JS**. Maybe your article is really helpful and many users have a high success rate trying it. Then users will look for more articles from you.

So there is a **83%**(yes this is from How I Met Your Mother) chance that a user is going to check more of your content if he/she likes the current one. You should give him/her an easy access to other content of yours right after the current article!

Adding next-previous post link or related post link is a good way to engage your audience with more posts and if the posts are good then the audiens may turn into subscribers.

## How to add Related Posts link in Jekyll?

Jekyll has a variable to show the related posts (up to 10). But the problem is that they are just a list of your latest posts that's all. I have no idea why they chose to call it **related posts**. It must be called **recent posts**.

But anyway it is a great way to let users know about your latest articles. It can be improved with some complex process of category wise matching. But I will write a detailed post in the update. For now refer to this [thread](http://stackoverflow.com/questions/10906574/filter-site-related-posts-in-jekyll){:rel='nofollow'}{:target="_blank"}.

Here is the code I have used on my [chess blog](https://kidschessworld.com){:target="_blank"}.

{% highlight html %}
<div class="related">
          <h2>Related Posts</h2>
          <ul>
            {% raw %}{% for post in site.related_posts limit:3 %}{% endraw %}
              <a href="{% raw %}{{ post.url }}{% endraw %}">
                  <li>
                  <h3>{% raw %}{{ post.title }}{% endraw %}&nbsp;&nbsp;{% raw %}{{ post.date | date_to_string }}{% endraw %}</h3>
                  </li>
              </a>
            {% raw %}{% endfor %}{% endraw %}
          </ul>
</div>
{% endhighlight %}

The output should look like the screenshot below

![Related posts jekyll]({{ site.url }}/images/related-posts-jekyll.jpg){: .full}

When you implementing this, make sure you tell Jekyll to paginate your posts by changing the parameters in **_config.yml**.

{% highlight html %}
paginate: 6
paginate_path: /page:num/
{% endhighlight %}
This way you are asking Jekyll to load 6 posts per page. First 6 will be loaded in the index(or wherever you call it), next 6 will be loaded in the url ``/page-1/``, next 6 in ``/page-2/`` and so on.


Also make sure you do the following change while loading posts.

{% highlight html %}
{% raw %}{% for post in site.posts %}{% endraw %} 
{% endhighlight %}
should be changed to 
{% highlight html %}
{% raw %}{% for post in paginator.posts %}{% endraw %}
{% endhighlight %}

{% include adsense-inside-post.html %}

## How to add Prev-Next Post links in Jekyll?

I think it is a better thing to insert **Previous-Next Post link** after an article than **related post link**. If you are writing articles around only one topic then this is ideal since you always write related articles. 

If there is a big article which has many parts in it and you are writing those parts in consecutive articles even then next and previous post links is the best choice.

Here is the code how I have implemented previous next links in my Jekyll blog.

{% highlight html %}
<div class="Previous-next">
  {% raw %}{% if page.previous.url %}{% endraw %}
    <a class="previous" href="{% raw %}{{page.previous.url}}{% endraw %}">&laquo; {% raw %}{{page.previous.title}}{% endraw %}</a>
  {% raw %}{% endif %}{% endraw %}
  {% raw %}{% if page.next.url %}{% endraw %}
    <a class="next" href="{% raw %}{{page.next.url}}{% endraw %}">{% raw %}{{page.next.title}}{% endraw %} &raquo;</a>
  {% raw %}{% endif %}{% endraw %}
</div>
{% endhighlight %}
That should look some what like the below screenshot.

![Related Previous-Next Navigation in Jekyll]({{ site.url }}/images/how-to-add-related-next-previous-post-to-jekyll.jpg){: .full}

Remember, the latest post will not have ```page.next``` since it is the last post and likewise the first post will not have ```page.previous```.

May be you have to style the links so that they appear in two directions or at least a little apart.

{% highlight css %}
    .next {
        float: right;
    }
{% endhighlight %}

Change your code accordingly to make it responsive. 

You can also use the code as a template that can be called anywhere on your blog. Read Step 4 of [**How to add Comments on Jekyll**](/jekyll-comments/#step4){: target="_blank"} to implement related post as a template.
{: .g}

I hope this article has helped you to make a navigation link of your own in your Jekyll blog. Let me know if you have any doubts. Subscribe for updates on upcoming articles.

Thanks for reading!