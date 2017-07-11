---
title: Jekyll Pagination
desc: Jekyll pagination can be easily implemented if correct methods are followed. I often see people asking me why they see a blank page when pagination is implemented. I will be discussing those issues in this article.
author: sharathdt
tags: Jekyll Plugins
image: jekyll-pagination.png
layout: post
permalink: /jekyll-pagination/
sec: wj
---

Pagination is the sequence of numbers assigned to pages in a book. In Jekyll however, each page can have multiple articles. This is a good way of organizing blog posts.

* Do not remove this line (it will not be displayed) 
{:toc}

## Why pagination?

The application is similar to how books do not have one long single page like a toilet paper. Books have pages. That makes it handy. Having all the pages in one page may be ok if you have few number of posts. But, if you have hundreds of posts, then it is not a good idea to show all those posts in a single page

{% include adsense-inside-post.html %}


## Pagination can be used only for Posts
Though Jekyll has different items like pages and collections, only Posts can have pagination. This might change in the future.

## Pagination can be done only on index.html
Jekyll recognizes pagination defined on ``index.html``. So if you want pagination on ``domain.com/blog/`` then you should create a folder with the name ``blog`` and create an ``index.html`` file inside it where you can define pagination. This is not enough, you should also define pagination value in configuration file as ``paginate_path: "/blog/page:num/"``.

For pagination on ``/blog/``, use ``paginate_path: "/blog/page:num/"`` in the configuration.
{: .r}


## How to use Pagination in Jekyll?
Adding pagination is not easy when compared to WordPress. WordPress usually paginates by default. Jekyll doesn't offer that. But Jekyll provides a code snippet that you can use in your blog. This snippet can be modified for our use.

Read: [Pagination](https://jekyllrb.com/docs/pagination/){: target="_blank"}

But just a copying the code will not work. There are some things to be taken care of before that.

### Define Pagination gem in configuration
Pagination used to be innate for Jekyll. But, then it was removed and made into a gem which can be used if required.

So define the gem in **_config.yml** as shown,
{% highlight yml %}
gems: [jekyll-paginate]
{% endhighlight %}

### Define Pagination in configuration
In the configuration file ``_config.yml``, copy the following,

{% highlight yml %}
paginate: 6
paginate_path: /page:num/
{% endhighlight %}

The above statement says that one page will have 6 posts and the naming of consecutive pages will be ``/page2/``, ``/page3/`` and so on.

paginate_path should be defined as ``/blog/page:num/`` if you are trying to paginates posts in a page ``/blog/``. [Go here](#pagination-can-be-done-only-on-indexhtml) for more details. 
{: .r}

Click on the below link to see a sample [_config.yml](https://raw.githubusercontent.com/sharu725/bare-minimum/master/_config.yml){: target="_blank" rel="nofollow" } file which is setup for pagination on every 5 posts.

## Use paginatior.posts

Now, open ``index.html`` file. If you have ``index.md`` instead, then rename it to ``index.html``. Pagination works only on HTML pages.

While listing the posts, ``paginator.posts`` should be used instead of ``site.posts``.

{% highlight html %}{% raw %}

<!-- post list -->
{% for post in paginator.posts %}
<li><a href="{{post.url | prepend: site.baseurl}}"><h3>{{post.title}}</h3></a></li>
{% endfor %}


<!-- pagination -->
{% if paginator.total_pages > 1 %}
<div class="pagination"> 
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a>
  {% else %}
    <span>&laquo; Prev</span>
  {% endif %}

  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
      <span class="webjeda">{{ page }}</span>
    {% elsif page == 1 %}
      <a href="/">{{ page }}</a>
    {% else %}
      <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  {% endfor %}

  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a>
  {% else %}
    <span>Next &raquo;</span>
  {% endif %}
</div>
{% endif %}

{% endraw %}{% endhighlight %}

Also, add some style so that the pagination looks good.

{% highlight css %}

.pagination a, .pagination span {
    padding: 7px 18px;
    border: 1px solid #eee;
    margin-left: -2px;
    margin-right: -2px;
    background-color: #ffffff;
    display: inline-block;
  }

.pagination a {    
    &:hover {
        background-color: #f1f1f1;
        color: #333;
    }
 }

.pagination {
    text-align: center;
 }

{% endhighlight %}

That should render something like this,

![Jekyll Pagination Example](/images/jekyll-pagination-example.png)


If you are looking for simple post suggestions at the end of every post, then please refer to these articles.

Read: [How to add previous next posts](/related-post-jekyll/){: target="_blank"}

Read: [How to add related posts](/jekyll-related-posts/){: target="_blank"}
{% include adsense-inside-post-2.html %}

If you observe a blank page after implementing Jekyll pagination, then you must have missed one or more steps I have mentioned here. 

Let me know if you could successfully implement pagination on your blog. If not please comment and let me know the issue.