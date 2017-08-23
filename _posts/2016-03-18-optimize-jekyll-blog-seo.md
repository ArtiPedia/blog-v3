---
title: 9 Must do Jekyll SEO optimizations
desc: Jekyll SEO (Search Engine Optimization) is something I struggled hard to figure out since I moved from WordPress. Initially,it was hard but gradually I found out that we can do a lot of things using liquid syntax.
keywords: 
author: sharathdt
tags: SEO Jekyll
image: Jekyll-SEO.png
img-src: "http://www.freepik.com/free-vector/seo-analytics_764868.htm"
img-src-name: Design by Freepik
layout: post
redirect_from: 
    - /optimize-jekyll-blog-seo/
    - /how-to-optimize-jekyll-blog-for-seo/
permalink: /optimize-jekyll-seo/
---


## Why SEO for Jekyll?
SEO is the only way through which you can get organic traffic. Organic traffic is usually better than paid traffic because in organic traffic the user is actually interested in the service you are offering.

I have used WordPress for a long time. If you ask me which one among WordPress and Jekyll is good for SEO, I would tell WordPress without a doubt. 

It is true that WordPress is optimized for SEO by default. And with plugins like Jetpack, Yoast and Schema Creator, WordPress is almost unbeatable by Jekyll. Ok wait, why am I praising WordPress so much when I should be discussing Jekyll SEO?

* Do not remove this line (it will not be displayed) 
{:toc}

At the moment we have Jekyll 3.5 and a small [list of Jekyll plugins](https://jekyllrb.com/docs/plugins/#available-plugins){:rel='nofollow'}{:target="_blank"}. We can depend on some of these plugins for SEO and most of the search engine optimization can be done without them. 

I will be discussing only the steps that involve making changes to your Jekyll functions but not to your content. That means I will not be addressing anything on Keyword Research, Link Building, Marketing etc.,
 
{: .clear}
 
## What is required in a Jekyll website for SEO?

There are many search engines that consider many different factors for indexing and ranking. I will mostly be concentrating on Google as 80% of all the searches are done over Google or Googled!.

![Jekyll Seo Joke](/images/seo-joke.png)

Google takes around 200 parameters into account in ranking a web page. But before we rank in Google we should focus on how to properly get indexed on Google database. 

**Remember:** Only indexed pages can be ranked!

{% include adsense-inside-post.html %}

## Let's dive into Jekyll SEO

We have to take care of some basic things that help us index our website on Google. How do we know whether our website is indexed or not? 
It's easy, just Google ```site:yourwebsite.com```. If you see your website links then it is already indexed. Check if the links you see in search results are working. 

I have given some of the important parameters (among around 200 of them) your Jekyll blog should have to index and rank better in Google.

**1. Title & Description**

**2. URL Structure**

**3. Sitemap**

**4. Image alt Tags**

**5. Connecting with Social Media**

**6. Open graph and Twitter cards in Jekyll**

**7. Favicon & Touch icons**

**8. Canonical URL**

**9. Responsiveness (mobile friendly layout)**


The list is big, so is the article! But follow these and I can assure you that your blog will be 60% optimized for SEO already. The rest depends on your efforts on content creation, link building , marketing etc.,


### Update 
Most of these can be implemented by using tag called {% raw %}{% seo %}{% endraw %} in the ``head`` section. This requires to add a gem in your **_config.yml** like this ``gems: [jekyll-paginate, jekyll-seo-tag]``. I'm assuming that you are using paginate gem also.  
{: .y}

This gem will add almost all the tags required for SEO. Thanks to [Ben Balter](https://github.com/benbalter){:rel='nofollow'}{:target="_blank"} for the awesome plugin. You can check it out [here](https://github.com/jekyll/jekyll-seo-tag){:rel='nofollow'}{:target="_blank"}. If you want to unserstand or implement all the tags on your own, then keep reading.

Let's implement head tags one by one in Jekyll.

## 1. Title and Description

A Title should match its description and the content of the article.

![Title and description jekyll seo](/images/jekyll-seo-meta-description.jpg)
{: .right .half}

Every blog post should have a unique title and description. Many bloggers do not bother having a unique description. If you don't specify one then Google will consider the first paragraph of the page(or post) as the description and show it in the search result snippet.

This may not always be accurate. I recommend using a custom description which will have the main keyword and briefly describes the whole article.
<div class="clear"></div>

![Jekyll seo meta description](/images/jekyll-seo-meta-description-wrong.jpg)
{: .left .half}
Consider this snippet. It doesn't make sense. Does it? 
So take a little while to give a proper description to all your posts. Viewers should be compelled to click on it when they read the description. So try to write a catchy but also a related description. They should know what they are getting into.

Search Engine bots try to fetch your _Title_ and _Description_ from the head tag first. So make sure you keep it there for them to crawl.
{: .clear}

### Title

Having your post title as the title makes sense. ```page.title``` variable takes care of that. If it is your homepage then there is no ```page.title``` variable available. We have to add an alternative which is your ```site.title``` that you may have mentioned in **_config.yml** file.

{% highlight html %}
<title>
   {% raw %}{%if page.title %}{% endraw %}
       {% raw %}{{ page.title }}{% endraw %}
   {% raw %}{% else %}{% endraw %}
       {% raw %}{{ site.title }}{% endraw %}
   {% raw %}{% endif %}{% endraw %}
</title>
{% endhighlight %}

Make sure you add the keyword in the title. For example for this post I have added **Jekyll SEO**.
{: .g}

### Description

Using page excerpt as a description is not a good idea because you may have something totally different in the first paragraph before you discuss on the main topic. If it is your homepage then make sure you have a site description mentioned in your **_config.yml** file.

Also, it is advised to restrict your description to 160 characters or less. Anything more can be considered spam or keyword stuffing by search engines. And a description is not considered for ranking but only to show snippets in the search results.

{% highlight html %}{% raw %}
<meta itemprop="description" name="description" content="{% if page.description %}{{ page.description | truncate: 160 }}{% else %}{{ site.description | truncate: 160  }}{% endif %}" />
{% endraw %}{% endhighlight %}

So that takes care of _Title_ and _Description_. But remember, you have to explicitly add Title and Description in the Front Matter to all your posts as shown in the example below. It doesn't matter how long your description is in the Frontmatter. It will be truncated to 160 characters in the meta tag.

Add your keyword at the beginning of the description so that users can easily find it on google search results. This usually gets more click through rates.
{: .y}

{% highlight css %}
---
title: How to Create a Beautiful Jekyll Blog?
description: I created this beautiful looking Jekyll blog by forking a repository. You can also fork it to make it yours. Jekyll is a simple blog generator. The community is growing and the number of plugins is also growing. I have moved all my blogs to Jekyll!
---
{% endhighlight %}


You must be thinking where the hell is **meta keywords**. It is not important anymore. Due to keyword stuffing - after 2009 - [**search engines are not considering meta keywords**](https://webmasters.googleblog.com/2009/09/google-does-not-use-keywords-meta-tag.html){: target="_blank"} for ranking.  
{: .r}


## 2. URL structure
A URL conveys a lot of information about the content. Users and bots expect it to be in sync with the topic.

### Make it readable
 
<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 800 500" enable-background="new 0 0 800 500">
<rect fill="#F1F1EC" width="800" height="500"/>
<text transform="matrix(1 0 0 1 141.876 107)" fill="#423F40" font-family="sans-serif" font-weight="bold" font-size="73">URL Readability</text>
<text transform="matrix(1 0 0 1 63 224)" fill="#4282C4" font-family="sans-serif" font-weight="bold" font-size="18">http://webjeda.com/how-to-create-a-jekyll-blog/</text>
<text transform="matrix(1 0 0 1 63 296)" fill="#169647" font-family="sans-serif" font-weight="bold" font-size="18">http://webjeda.com/create-jekyll-blog/</text>
<text transform="matrix(1 0 0 1 63 368)" fill="#CC203B" font-family="sans-serif" font-weight="bold" font-size="18">http://webjeda.com/2ey9845n/rem?=viral?id=39</text>
<line fill="none" stroke="#A7A9AC" stroke-width="2" stroke-miterlimit="10" x1="486" y1="189" x2="486" y2="393"/>
<text transform="matrix(1 0 0 1 538.832 209)"><tspan x="0" y="0" fill="#4182C4" font-family="sans-serif" font-weight="bold" font-size="18">I’m sure what I will get </tspan><tspan x="30.104" y="21.6" fill="#4182C4" font-family="sans-serif" font-weight="bold" font-size="18">if I click on this.</tspan></text>
<text transform="matrix(1 0 0 1 535.1963 286)" fill="#159647" font-family="sans-serif" font-weight="bold" font-size="18">I think I can click this.</text>
<text transform="matrix(1 0 0 1 510.6172 359)"><tspan x="0" y="0" fill="#CC203B" font-family="sans-serif" font-weight="bold" font-size="18">This looks way too confusing. </tspan><tspan x="8.738" y="21.6" fill="#CC203B" font-family="sans-serif" font-weight="bold" font-size="18">Maybe I shouldn’t click this.</tspan></text>
</svg>


A clean URL structure gives a better click through rate. Nowadays, search engines are smart enough to detect whether the URL has any relation with the content.
I have seen many blogs whose URL contains page ids in it. This will not convey any good information to either a human reader or to a search engine bot. It is only used for the convenience of differentiating all the pages within a blog. Do not use **ids** in URL.

Including date is a choice. You can opt it if you think it will help users in some way. Search engines may extract this data. It is useful if dates really matter to your content.
{: .clear}

Imagine you are a comic book reviewer. You review Iron Man comic every month then it would be a great idea to have URLs like this

```http://webjeda.com/2016/01/21/iron-man-comic-review```

```http://webjeda.com/2016/02/21/iron-man-comic-review```

```http://webjeda.com/2016/03/21/iron-man-comic-review```

Users will know - just by looking at the URL - which comic you are referring to. The ```date``` is included in the URL by default in Jekyll. If not add the following code to **_config.yml** file.
{% highlight yml %}
permalink: date
{% endhighlight %} or {% highlight yml %}
permalink: pretty
{% endhighlight %}

To take it out, use the following code

{% highlight yml %}
permalink: /:title/
{% endhighlight %}


### Stop using stop-words!
Using **and, or, but, of, the, a, etc** inside a URL is not necessary. It will only increase the length of your URL(bots like short URLs). In this post, I have left out **how-to** because the URL still makes sense without those stop words. Take some time to leave stop words before you decide to publish a post. 

In Jekyll, a URL can be changed by renaming the file in ```_posts``` folder.

```2016-03-09-optimize-jekyll-blog-seo.md``` is a better name than

```2016-03-09-how-to-optimize-jekyll-blog-for-seo.md``` 


whose respective URLs would be

```http://blog.webjeda.com/optimize-jekyll-blog-seo/```

```http://blog.webjeda.com/how-to-optimize-jekyll-blog-for-seo/```

{% include adsense-inside-post-2.html %}

Try to fit in the keyword in the URL as well but make it short and precise.

## 3. Sitemap
Having a sitemap is a necessity these days. It helps bots to crawl through your website easily. Also, submit sitemaps to search engines so that they don't have to look for it in the first place. 

Read all about why we should use a sitemap and how to submit a sitemap to Google here [How to create a sitemap for Jekyll blog](/jekyll-sitemap/){:target="_blank"}. Submitting sitemap and tracking how much of it has been indexed is an important task in SEO. Do not ignore this step.

Leave a link of the sitemap at the footer so that if your homepage is crawled by a search engine bot, it will follow the sitemap and may crawl more pages.
{: .g}

## 4. Image alt Tags

Alt-tags are nothing but text shown in case if the image does not load. This tag is read by bots. So make use of this opportunity and include alt-tags with keywords in all of your images(even the logo). 

{% highlight html %}
<img alt="jekyll seo" title="Jekyll SEO" src="/images/jekyll-seo.jpg">
{% endhighlight %}

Also, be sure to use a related alt tag. This helps search engines to know what's in the image since they are not smart enough to make sense out of an image(yet). 


## 5. Connecting with Social Media

Connecting to social media can be achieved by having a share option at the bottom of your posts. Read [How to add a share box to Jekyll](/share-buttons-jekyll/){:target="_blank"}.


## 6. Open graph and Twitter cards in Jekyll
A better way to optimize your social sharing is by adding Open Graph and Twitter Cards tag to your ```head``` section. 

### Why do you need Open Graph anyway?
Open Graph is found by facebook as a way to understand a link better. When you share your website link, there are chances that some things may miss out or some unwanted data is being detected. In order to avoid this and for your link to be better recognized by social media sites, you have to implement Open Graph.

Open Graph tags for Jekyll 
{% highlight html %}{% raw %}
<meta property="og:locale" content="en_US">
<meta property="og:type" content="article">
<meta property="og:title" content="{%if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}">
<meta property="og:url" content="{{ site.url }}{{ page.url }}">
<meta property="og:image" content="{{ site.url }}/thumbs/{{ page.image }}" />
<meta property="og:site_name" content="WebJeda Blog">
<meta property="article:publisher" content="http://www.facebook.com/webjeda" />
<meta property="article:author" content="https://www.facebook.com/sharu725" />
<meta property="article:published_time" content="{{ page.date }}" />
<meta property="og:description" content="{% if page.description %}{{ page.description }}{% else %}{{ site.description }}{% endif %}">
{% endraw %}{% endhighlight %}




Twitter Card tags for Jekyll
{% highlight html %}{% raw %}
<meta name="twitter:card" content="summary_large_image"/>
<meta name="twitter:title" content="{%if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}">
<meta name="twitter:description" content="{% if page.description %}{{ page.description }}{% else %}{{ site.description }}{% endif %}">
<meta name="twitter:site" content="@webjeda" />
<meta name="twitter:creator" content="@sharathdt">
<meta name="twitter:card" content="summary">
{% endraw %}{% endhighlight %}


You can add many other tags as per requirement by referring to [Open Graph](http://ogp.me/){:rel='nofollow'}{:target="_blank"} and [Twitter Cards](https://dev.twitter.com/cards/overview){:rel='nofollow'}{:target="_blank"} documentation.



## 7. Favicon & Touch icons
![Favicon Jekyll SEO](/images/favicon-jekyll-seo.JPG)
{: .right .half}
A favicon is a ```.ico``` file usually of the dimensions 16x16. This is what most of the users remember of your site. It should represent your website in some way so that when a user sees this favicon in his bookmark bar, he should reconcile that it is your website.


Touch icons are basically for hand-held touch devices. They show up in the browser homepage when you bookmark a website.
{: .clear}

![Touch icons Jekyll seo](/images/touch-icons-jekyll-seo.jpg)
{: .left .half}
This is how an android browser shows touch-icons when you bookmark a website or visit a website very often. 
If there is no icon available then it shows default icon or first letter of the domain.

Use the below code to implement touch icons.
{: .clear}

{% highlight html %}
<link rel="apple-touch-icon-precomposed" href="/img/apple-touch-icon-iphone-60x60.png">
<link rel="apple-touch-icon-precomposed" sizes="60x60" href="/img/apple-touch-icon-ipad-76x76.png">
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="/img/apple-touch-icon-iphone-retina-120x120.png">
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="/img/apple-touch-icon-ipad-retina-152x152.png">
{% endhighlight %}

But it is a pain creating all those images. So there is a web app that can do the job for you along with the code and a favicon. All you need to do is to provide a high quality, square shaped logo.

Use [Iconifier](http://iconifier.net/){:rel='nofollow'}{:target="_blank"}.
Download the **zip** file it generates to get all icons along with the code.

Do not use too many touch icons in the head tag. It may slow down your website performance. Three to four icons with different sizes should be enough.  
{: .r}

## 8. Canonical URL
You should not be serving the same content on different URLs. Even if those URLs do not look very different, a search engine bot considers them as different.

```http://blog.webjeda.com/free-domain-email-zoho/```

```http://blog.webjeda.com/free-domain-email-zoho/index.html```

The above URLs may redirect to the same content. This will look like duplicate content to bots and one of them may be punished or may take forever to rank higher.

So use canonical tag inside your head tag like this

{% highlight html %}
<link rel="canonical" href="{% raw %}{{ page.url | prepend: site.url }}{% endraw %}">
{% endhighlight %}

This is a way of telling the Search Engine bots that your content is only available at one URL.


## 9. Responsiveness (mobile friendly layout)
After April 21st 2015, Google made responsiveness as a SEO parameter for ranking. You may observe the term **Mobile friendly** on search results on smart-phones.

Test you website for mobile fridliness using [Mobile Friendly Test](https://www.google.com/webmasters/tools/mobile-friendly/){:rel='nofollow'}{:target="_blank"}.
If you find any errors then try to solve them.

Read all about how your responsive website should be - [Mobile responsiveness](https://developers.google.com/webmasters/mobile-sites/mobile-seo/){:rel='nofollow'}{:target="_blank"}.

Usually, almost all the Jekyll themes (even the default theme) are responsive. If you are designing a new layout for your requirements then make sure you use proper media queries to adjust the layout to smaller screen sizes.

Media query detects the screen-size and applies the CSS that you provide inside it. That's all it does.

If you are not sure how to use them, then no problem. Start here - [w3-schools](http://www.w3schools.com/css/css_rwd_mediaqueries.asp){:rel='nofollow'}{:target="_blank"}. 

### Conclusion: 
Though Jekyll users have a hard time configuring SEO on their own, they do have the full control. Jekyll does only the things that you tell it to do. Features like AMP Pages, htaccess, robot.txt are either not available or not explored well on Jekyll but we can hope that in the coming years those features will be available by default.

Google is leaning more towards **User Experience Optmization**. So make sure that surfing your website is a smooth experience even on low bandwidth. Look at your content from a user perspective. If you have unique and useful content (not copied from elsewhere) then your website will definitely rank better.

If you want to test whether your website is optimized for SEO then try [**SEO Checkup**](https://varvy.com/){: target="_blank" rel="nofollow"} and try to resolve all the errors and warnings.
{: .g}

I hope you got a fair idea on how to perform some quick SEO to your Jekyll blog. There are many advanced SEO parameters for Jekyll which I will be discussing in a future post. Let me know if you come across any problems while implementing these SEO methods I have mentioned in the article.

Thanks for reading!