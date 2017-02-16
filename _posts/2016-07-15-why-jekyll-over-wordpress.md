---
title: Why did I choose Jekyll over WordPress?!
desc: Jekyll will be taking over a significant share among all the blogging platforms. I chose a simple static CMS - Jekyll over world's most famous CMS - WordPress! There are reasons why I made this choice and I have tried to put them before you.
author: sharathdt
tags: Opinion Jekyll
image: why-jekyll-over-wordpress.png
img-src: "http://www.freepik.com/free-vector/fist-coming-out-of-cracked-ground_720279.htm"
img-src-name: Design by Freepik
layout: post
---


A long time ago I had few blogs that were running on WordPress. I bought domain names and a reliable hosting space to keep them running. WordPress blog is very easy to set up. There are thousands of themes and plugins for all kinds of looks and functionalities.

**But, what's wrong?**
{: .r}

# WordPress

## 1. Heavy!
WordPress is heavy. By saying heavy what I mean is that it has a lot of code in it. Even a minimal WordPress blog will have too much code. Take a minimal theme from WordPress and compare it with my theme [Thunder](http://webjeda.com/thunder/) or any Jekyll theme. You will observe a significant difference in size when you view source.

Using a lot of plugins can lead to this problem. WordPress bloggers don't usually realize whether the website is slowed down by a plugin. The reason may be is that they are using a fast internet connection. For them the website still loads quick but when it comes to a slower data connection, the real face(pace) of the website is seen!

Google Chrome has a nice inspection option called Network Throttling where you can simulate a slow internet connection on your browser! 

* Do not remove this line (it will not be displayed) 
{:toc}


## 2. Slow
This is the by-product of being heavy. More the code slower the website. WordPress has some frameworks that make it light and fast but doesn't come anywhere close to Jekyll's simplicity.


## 3. Difficulty in writing Posts
If you have written posts on WordPress then you know what I'm talking about. It almost always is online. There are offline apps to write blogs but then you will have to test it online. It is not a big deal. Actually, WordPress has image drag and drop option which is so much easier than Jekyll. But Jekyll stands out because of its Markdown support by default. 

Editing in markdown is addictive!
{: .r}

## 4. Hosting cost
WordPress needs a hosting which supports ``php`` and ``mySQL``. So, it is comparatively costly to host. Jekyll being static can be hosted for cheap on static file hosting providers or for free on Github!
Read: [How to create a Jekyll blog](/create-jekyll-blog/){: target="_blank"}

## 5. Design restrictions
This is actually the key reason to migrate from WordPress. WordPress has a lot of themes and plugins to choose from but if you want to change something, say you want the logo to be some pixels down then it becomes a hassle.

## 6. Distractions
If you have ever visited a WordPress site (I bet you've) you will see something like this happening.

![WordPress Distractions](/images/why-I-hate-wordpress.png){: .noborder}

Since WordPress is easy to use and there are gazillion plugins available to do these kind of pop-ups, top-bars and other ridiculous bars. Many people use these features as they like, screwing up their readers experience.

May be it is good with most users but when I see a pop-up I will look for the close button before reading anything on it. 
{: .y}

The worst thing you can do to someone who's reading your blog is to distract them. Let them read the damn thing. They may have googled something, found your website link, clicked on it for help. You should be lucky that they landed on your website because there at least 10 different websites offering the same content. If they like what you write then they definitely will subscribe.

These days with all those spam emails cluttering my inbox, I don't like to give up my email address to anyone. Last time I was reading [Oliver Emberton's blog](http://oliveremberton.com/){: target="_blank" rel="nofollow"} and it was a nice experience. Though the website is made using WordPress, it wasn't distracting at all. It was rather intriguing. I ended up subscribing to his blog without any such intervensions.


<p></p>

**What's so good about Jekyll?**
{: .g}

# Jekyll

## 1. Simple
Jekyll has no database! Jekyll runs nothing on the server. It just keeps files ready to be served. Jekyll is really simple once you understand the basic structure and functions. It supports markdown for posts and pages. It uses the famous **Liquid Syntax** by shopify for conditional logic and other functionalities which is basically human readable coding! I think this way of coding is very comprehensive even to a non-coder.


## 2. Light, fast and secure
Since Jekyll has very less code, it is fast by default, it is fast. If you want to see the difference then take a Jekyll site (take this site for example) and a WordPress site and compare them on [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/){: target="_blank" rel="nofollow"}.

Having no database is kind of good when we are looking at security. **Static** sites are way more secure than **Dynamic** ones. Static sites are almost unhackable.

## 3. You are in control!
You are responsible for even a single extra space added to the code! So you have the complete control of the website or blog. This also means that you can easily minify, compress all the assets as you like.

{% include adsense-inside-post.html %}

Eventually, I switched all my blogs to Jekyll and I always have a local copy of my blog which wasn't easy to have in WordPress. I'm pretty happy with the performance of my blogs. For example, my chess blog [kidschessworld](http://kidschessworld.com){: target="_blank"} is built using Jekyll and hosted on Github Pages which has helped me gain some business(I teach chess online).

You don't have to worry about the design part. There are hundreds of themes already available. You can [subscribe](http://eepurl.com/bZdvSP){: target="_blank" rel="nofollow"} to my blog to get a detailed list of free responsive Jekyll themes and their links. 

# Start here
Usually, Jekyll is hosted on github pages but you can also host it on any other conventional hosting service. But one thing you observe is that, all the Jekyll themes are put in a github repository. So to test it out you should know how to fork(copy) them to your own account. To do that, you should have a github account. So [sign up for a free account](https://github.com/join?source=header-home){: target="_blank" rel="nofollow"}.

Once that is done, you have to find a nice theme for your blog. So do some research or [sign up here](http://eepurl.com/bZdvSP){: target="_blank"} to get a quick checklist. You can also checkout [themes section](/jekyll-themes/){: target="_blank"} in my blog. Now you should visit the theme's homepage. Here is a video guide.

<iframe class="video" src="https://www.youtube.com/embed/T2nx6tj-ZH4?rel=0" frameborder="0" allowfullscreen></iframe>

## Use a theme that suits your needs
Jekyll has a pretty large community now. There are people creating awesome themes. I suggest going through [Jekyll Themes](http://jekyllthemes.org){: target="_blank" rel="nofollow"} or my [Theme section](/jekyll-themes/){: target="_blank"} and find the one that suits your needs.

## Understand baseurl
Now you have the theme file hosted on some URL. You can make changes to this by editing most of the files in the repository. But you should be careful while editing **_config.yml**. Many beginners edit the ``baseurl:`` to something and get 404 error!

To avoid this, you should understand why is it used. Baseurl is the base of your repository where the files are located. If your repository name is ``jekyll-blog`` then your baseurl is ``/jekyll-blog``.

## Understand Jekyll file structure
If you observe the forked repository, it will have some folders with names starting with an underscore. These folders are meant for certain things. For example ``_posts`` is where all the posts should reside.

Read [Layman's Guide to Jekyll](http://blog.webjeda.com/jekyll-guide/){: target="_blank"} for a good insight.

## Write more posts
Jekyll offers markdown support. So you can edit your blog posts in markdown and Jekyll will convert it into html. You can use prose.io to write your posts on the go, even from a smartphone. Read [How to edit or add Jekyll posts through Browser using Prose](http://blog.webjeda.com/edit-posts-jekyll/){: target="_blank"}.

## Use a custom domain name for your blog
Your blog may be hosted with a URL ``http://username.github.io`` which is a third party domain. If you want to use your own domain name then read [How to add a custom domain name to Jekyll blog](http://blog.webjeda.com/custom-domain-github/){: target="_blank"}. Though the procedure is for github pages, the same thing applies to Jekyll blog.


## Create a contact form for your Jekyll blog
Beginners try php forms inside Jekyll and see that it doesn't work. It doesn't because Jekyll doesn't execute code on the server. So restrain yourself from using ``php``. Since Jekyll blog is a static site, you should use something that works on a static website. Read [How to create a contact form in Jekyll](http://blog.webjeda.com/jekyll-contact-form/){: target="_blank"}.


## Create a subscribe form for your Jekyll blog
Maintaining a mailing list is good for initial traffic. Mailchimp forms can be used inside Jekyll. I hope even Aweber forms can be used in Jekyll (I haven't tried Aweber). Read [How to create a mailchimp subscribe form in Jekyll](http://blog.webjeda.com/jekyll-subscribe-form/){: target="_blank"}.

{% include adsense-inside-post-2.html %}

## Make your blog super fast!
Faster websites keep users happy. Your blog is already fast because you are using Jekyll but you may have too many things loading up or have heavy media files. For a fast Jekyll blog read [How to speed up Jekyll blog](http://blog.webjeda.com/jekyll-speed/){: target="_blank"}.

## Optimize Jekyll blog for SEO
Now your blog is ready to rock. But let's find some organic traffic. Read [How to optimize Jekyll blog for SEO](http://blog.webjeda.com/optimize-jekyll-seo/){: target="_blank"}.

## Secure your Jekyll blog with https
Using SSL on Jekyll blog will improve your search engine ranking! It also keeps users session safe. Read [How to get SSL certificate for Jekyll](http://blog.webjeda.com/jekyll-ssl/){: target="_blank"}.

# Conclusion
There are 100 other things you can do using Jekyll but for a beginner, the above tasks are enough to start off with. I don't think I will ever go back to WordPress. But I still suggest WordPress for non-technical people who do not want to touch a single line of code. Try Jekyll at least for fun and let me know how you felt.

I may have missed several points on WordPress and Jekyll regarding their advantages, disadvantages, user-friendliness etc. Let me know what is missing so that I can add to the list. 

Thanks for reading!