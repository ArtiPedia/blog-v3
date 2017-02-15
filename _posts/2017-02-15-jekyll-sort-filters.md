---
title: Jekyll Filters
desc: Jekyll filters like sort are used to modify the output in a certain fashion for our convenience. I have described a few methods to sort Jekyll posts by categories, tags and other front matter values.
author: sharathdt
tags: Jekyll Liquid
image: jekyll-sort-filter.png
img-src: "http://www.freepik.com"
img-src-name: Image by Freepik
layout: post
permalink: /jekyll-filters/
---


Jekyll Filters are a wide range of parameters that can be used to modify the output produced by Liquid tags or objects. I will be describing two Jekyll filters which can be very useful in sorting post index. One is **sort** filter and the other is **where** filter.

## Simple Filters
Consider this example. I'm modifying the output of the page variable ``page.author`` which is ``sharathdt`` using string filters.

{% highlight yml %}
{% raw %}{{page.author}}{% endraw %} = {{page.author}}
{% raw %}{{page.author | append: ' is a web designer'}}{% endraw %} = {{page.author | append: ' is a web designer'}}
{% raw %}{{page.author | append: ' is a web designer' | remove: 'dt'}}{% endraw %} = {{page.author | append: ' is a web designer' | remove: 'dt'}}
{% raw %}{{page.author | append: ' is a web designer' | remove: 'dt' | capitalize}}{% endraw %} = {{page.author | append: ' is a web designer' | remove: 'dt' | capitalize}}
{% raw %}{{page.author | append: ' is a web designer' | remove: 'dt' | capitalize | replace: 'is', 'is a good'}}{% endraw %} = {{page.author | append: ' is a web designer' | remove: 'dt' | capitalize | replace: 'is', 'is a good'}}
{% raw %}{{page.author | append: ' is a web designer' | remove: 'dt' | capitalize | replace: 'is', 'is a good' | truncate: 15 }}{% endraw %} = {{page.author | append: ' is a web designer' | remove: 'dt' | capitalize | replace: 'is', 'is a good' | truncate: 15 }}
{% raw %}{{ "<h1>Title of a post</h1>" | strip_html }}{% endraw %} : Title of a post

{% endhighlight %}

* Do not remove this line (it will not be displayed) 
{:toc}

What I have used above are simple string filters. They modify a string value. We need different way to handle array data produced by loops. 

Apart from these string filters, there are plenty of other filters that may come in handy in different situations. Check them out here: [Liquid Filters](https://help.shopify.com/themes/liquid/filters/string-filters){: target="_blank"}.

{% include adsense-inside-post.html %}

## Advanced Filters

I'm calling this advanced because these filters help us modify array outputs. An array is a set of multiple items. A **list of posts** that we generate in the index page is an array of posts. All the **categories** or **tags** we use in posts is an array.

Since these arrays are rendered inside a **for loop**, we cannot define filters right in the tag. We should filter the array first and then let it pass through the ``for loop``.
{: .g}

**Consider this example:** Generate a list of posts arranged in alphabetical order.

We know that Jekyll sorts all the posts by date. What should we do to arrange it by their title?

### Default Jekyll post list
Here is how a default post generation tag would look like. You can find this in almost all Jekyll blogs, mostly on the homepage.

{% highlight html %}{% raw %}
{% for post in site.posts limit: 5 %}
<ul>
<li>{{post.title}} - {{post.date | date_to_string}}</li>
</ul>
{% endfor %}
{% endraw %}{% endhighlight %}

I'm limiting the number of posts to only 5.

<pre>
{% for post in site.posts limit: 5 %}
<li>{{post.title}} - {{post.date | date_to_string}}</li>
{% endfor %}
</pre>


What we observe here is that the posts are arranged by date. The latest one being at the top.

Consider this example where I have sorted posts by their title.


### Sort Jekyll posts by title

We will be sorting the list first and then give it to the for loop for output.

{% highlight html %}{% raw %}
{% assign sorted-posts = site.posts | sort: 'title' %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
{% endraw %}{% endhighlight %}

#### Output
<pre>
{% assign sorted-posts = site.posts | sort: 'title' %}
{% for post in sorted-posts limit: 5 offset: 7 %}
<li>{{post.title}}</li>
{% endfor %}
</pre>


Let's arrange it in the **reverse order of alphabets**.

{% highlight html %}{% raw %}
{% assign sorted-posts = site.posts | sort: 'title' | reverse %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
{% endraw %}{% endhighlight %}

#### Output
<pre>
{% assign sorted-posts = site.posts | sort: 'title' | reverse %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
</pre>

What we see here is that the posts are rendered in reverse alphabetical order.


### Sort Jekyll posts by categories

Many times we want the posts to be divided into different categories and displayed as a list. This can be achieved by Jekyll's new filter - ``where``.

This filter is only available for versions Jekyll 2.5 or above.
{: .y}

Consider this website for example. Most of my posts are about Jekyll which will have a category ``jekyll``. I also write posts on web designing which will have a category ``Web-Design``.  Let's filter out all the posts that have a category **Web-Design**.

{% highlight html %}{% raw %}
{% assign sorted-posts = site.posts | where: "categories","Web-Design" %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
{% endraw %}{% endhighlight %}

#### Output
<pre>
{% assign sorted-posts = site.posts | where: "tags","Web-Design" %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
</pre>


### Sort Jekyll posts by type
Jekyll posts now can be sorted by any Front Matter. It doesn't have to be tags or categories. Let's consider the value ``author``. I have author mentioned in almost all my posts like below.

{% highlight yml %}{% raw %}
---
title: "Webjeda Jekyll Blog"
layout: post
author: sharathdt
categories: Jekyll Web-design
---
{% endraw %}{% endhighlight %}

Now, consider you have different authors who write articles on your blog. This can be a great way to separate posts from each author.

{% highlight html %}{% raw %}
{% assign sorted-posts = site.posts | where: "author","sharathdt" %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
{% endraw %}{% endhighlight %}

#### Output
<pre>
{% assign sorted-posts = site.posts | where: "author","sharathdt" %}
{% for post in sorted-posts limit: 5 %}
<li>{{post.title}}</li>
{% endfor %}
</pre>

Checkout other filters here: [Jekyll Filters](https://jekyllrb.com/docs/templates/#filters){: target="_blank"}

{% include adsense-inside-post-2.html %}

### Conclusion
Thanks to the developers at Github and other contributors who are adding new features to Jekyll which are making our lives easy. Sorting posts based on parameters other than categories and tags was a little hard. But now, with newly added filters, sorting is very easy. 

Let me know if this has worked for you. Post your suggestions and feedback in the comment section.


