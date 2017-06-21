---
title: Jekyll Redirect 301
desc: Jekyll 301 permanent redirection has become easy with the plugin jekyll-redirect-from which is now supported by Github Pages. Learn how to redirect 404 error pages that might help improve your SEO score.
author: sharathdt
tags: Jekyll Plugins
image: jekyll-redirect-301.png
img-src: "http://www.freepik.com/free-vector/cartoon-dinosaurs-pack_874040.htm"
img-src-name: Design by Freepik
layout: post
permalink: /jekyll-redirect/
---

Jekyll redirection is of grave importance if you are migrating from different platforms like WordPress, Blogger or Tumblr to Jekyll. It helps in controlling crawl(by search engine bots) errors and thus not affecting the SEO.

* Do not remove this line (it will not be displayed) 
{:toc}

I faced the necessity for Jekyll redirection when I had to shorten the links to some posts. At the time I changed it without redirecting the old link to the new one since I had no significant traffic. But social media shares that I did for old posts were still around. When the site got more traffic, people started to check out old posts through my twitter and facebook pages. That is when the 404 errors started popping up.

{% include adsense-inside-post.html %}

I use [**Google Search Console**](https://www.google.com/webmasters/tools/home){: target="_blank"} to track my website analytics. I recommend you to use this feature if you are looking for a better SEO.

![Jekyll redirect  301 permanent 404 errors](/images/jekyll-redirect-404-errors.png)

## Why Jekyll redirection? 

Initially, I had redirected the old posts using an older method. I had it in place for a long time. After some months, I thought those redirects are not necessary anymore and removed all them. I was so wrong! Keep the redirects in place forever!!

Users have a very low tolerance for 404 errors. And if they see two or more of them in a row then they may not return to your website. The errors ruin the credibility of a website unless you have a cool [404 error page](/404/){: target="_blank"} like I do. Just kidding, nothing but a 301 redirection can save the reputation.

404 errors will have a negative effect on SEO as well. I have seen my page rank getting a nose dive after too many 404 errors.
{: .r}

## How to redirect Jekyll URLs?
There are many ways to achieve this. One is through **.htacess** if your hosting supports Apache. For static hosting like Github Pages, the **jekyll-redirect-from** plugin comes in handy.

Let's assume that the hosting serves only static files.

### Declare jekyll-redirect-from gem in config file.
In the **_config.yml** file - similar to ``jekyll-paginate`` gem - mention ``jekyll-redirect-from`` plugin as well.

{% highlight html %}
gems: [jekyll-paginate, jekyll-redirect-from]
{% endhighlight %}

I'm hoping that you are using pagination as well.

If you are rendering the Jekyll site locally then make sure you install the plugin using ``gem install jekyll-redirect-from`` command.
{: .y}

### Redirect URLs
It is important to find the URLs that are hitting 404. A good way to find them is through Google Search Console.

Once you have a list of 404 URLs, copy one by one and put them in the post or page to which you want that URL should redirect to, as shown below. You can redirect multiple 404 URLs together.

{% highlight html %}
---
title: {{page.title}}
redirect_from: 
    - /some/404/url/
    - /another/404/url/
permalink: {{page.url}}
---
{% endhighlight %}


It creates a meta refresh page for every 404 URL. That will redirect to the original permalink.

![Jekyll 301 redirect](/images/jekyll-301-redirect-example.png)

This page will be shown for a second or so and then the page redirects to the original article.


If you would like to redirect the current page to a different website, then use this.

{% highlight html %}
---
title: {{page.title}}
redirect_to:
  - http://some-website.com
permalink: {{page.url}}
---
{% endhighlight %}

The result after implementing the Jekyll 301 redirect.

![Jekyll 301 redirect](/images/jekyll-301-redirect-404-errors.png)

{% include adsense-inside-post-2.html %}

## The .htaccess method
If your hosting supports Apache then this method can be used.

### Include .htaccess file
Since files with the name starting with a ``.`` is not recognized by Jekyll, you will have to explicitly mention it to be considered. Add this line on the **_config,yml**.

{% highlight html %}
include: [.htaccess]
{% endhighlight %}

### Create .htaccess
Create a ``.htaccess`` file at the root of the repository with the following code on it.


{% highlight html %}{% raw %}
---
---
DirectoryIndex index.html

RewriteEngine On
RewriteBase /


{% for post in site.post %}
  RewriteRule ^{{ post.old }} {{ post.permalink }} [R=301,L]
{% endfor %}
{% endraw %}{% endhighlight %}

### Add redirect front matter in posts
Add below permalink in the posts that a 404 link to be redirected to.
{% highlight html %}
---
title: {{page.title}}
old: /some/404/url
permalink: {{page.url}}
---
{% endhighlight %}

Do this for all the necessary posts. 

## Conclusion
Managing the website in a way that there will not be any 404 errors is the best way to be safe. But sometimes we make mistakes, we have to change things, move things. In such cases, 404 errors are bound to happen. But with a proper permanent redirection, these errors can be handled.


Let me know if the plugin worked out fine for you. Please share your thoughts in the comment section.

Refer: [JekyllRedirectFrom plugin](https://github.com/jekyll/jekyll-redirect-from)
