---
title: Simple Share Bar for Jekyll without JS!
desc: Reducing the use of JavaScript results in a faster loading speed. Here is a guide on how to add a social share bar to Jekyll blog. You can copy paste the code and it should work! Many Jekyll themes do not offer a good share bar. So I thought of making one for myself!
keywords: share bar without javascript, Jekyll share buttons, share buttons for Jekyll blog
author: sharathdt
tags: Jekyll SEO
image: share-bar-to-jekyll.png
layout: post
redirect_from:
    - how-to-add-share-buttons-to-jekyll/
    - how-to-add-share-buttons-to-jekyll
permalink: /share-buttons-jekyll/
sec: wj
---


## Why share bar for Jekyll blog?
If you read a lot over the internet then you know how hard it is to share an article with your friend if it doesn't have a share button. You have to copy the link from the address bar, go to your email account, type every single detail and send it. Same thing follows for sharing on social media websites.


* Do not remove this line (it will not be displayed) 
{:toc}


It is a good idea to have share buttons at the end of an article. Users may not be willing to copy paste the link but hitting a button is easy! More share is equal to more eyeballs on your article. Shares will drive traffic to your website and sometimes it may go viral. So it is necessary to provide an option to share.


## How to add a social media share bar?

Adding a share bar is really easy using services like **ShareThis** or **AddtoAny**. They are good. They provide decent buttons with share count. This is what I recommend if you just want a share bar and you don't care about your website loading speed. I have used ShareThis before and the problem was that it loads a lot of JavaScript files which will slow down the website.

I can always ```defer``` javascript loading but, the files that are loaded by ShareThis are from a remote server. So I don't even have that option. Then I thought of saving the remote JavaScript files into my local directory and call it from there! That didn't work out very well as there were session variables used and they started to throw ```Js``` errors.

Now I had to make a decision whether to use it or make one for myself. I thought why not make one! I will have the complete design control. So this is how I designed a share bar for my Jekyll blog.

## Making a social media share bar without JavaScript

When I decided to make a share bar for my Jekyll blog WebJeda, I thought of making it javaScript free. As a developer - for a fast performing website - you should avoid JavaScript as much as possible and also lower the number of http requests. With ShareThis, I used to have 5 to 6 JavaScript files being loaded from a remote server and 22 requests were made. This happens when you have many buttons and every button is downloaded remotely!

Once I installed my css-only share bar, the request number dropped to 11! That was a huge improvement! But it comes at a cost. I cannot see the number of shares anymore. I can always write a code myself to calculate the number of shares based on click event but that will be in the future. For now, I'm happy that I have a beautiful share bar which is made only with ``html`` and ``css``. You can see it in the screenshot.

{% include adsense-inside-post.html %}

## Basics before we dive in
When I was preparing this share bar, I was facing problems with sharing the page I'm currently browsing. Let's say you are in the page ``article-1``, the facebook share link should look like ```https://www.facebook.com/sharer/sharer.php?u=http://blog.webjeda.com/article-1/```. And if you are in the page ``article-2``, then it should change to ```https://www.facebook.com/sharer/sharer.php?u=http://blog.webjeda.com/article-2/```.


But how to make this change of URL for every page. One way was to use ```window.location()``` but that is again JavaScript which I'm trying to avoid. Then I realized that I can use **Site Variables** - the ```{% raw %}{{ stuff }}{% endraw %}``` inside double curly braces!

Here is an image explaining site variables for the link [How to create a Jekyll blog](/create-jekyll-blog/){:target="_blank"}. You can check the site description by viewing the source. These variables are mentioned inside ```_config.yml``` file.

![How to use site variables in Jekyll](/images/jekyll-site-variables.svg)


Check all the Jekyll [variables here](http://jekyllrb.com/docs/variables/){:rel='nofollow'}{:target="_blank"}.

Then I changed the facebook share link to the following which works for all pages!
{: .clear}

```https://www.facebook.com/sharer/sharer.php?u={% raw %}{{ site.url }}{{site.baseurl}}{{ page.url }}{% endraw %}```

How cool is that!

I can do the same thing for twitter share link

```https://twitter.com/home?status={% raw %}{{ site.url }}{{site.baseurl}}{{ page.url }}{% endraw %}```

This works pretty much on all the social media websites. For LinkedIn, I also added title and description of the page.

```https://www.linkedin.com/shareArticle?mini=true&url={% raw %}{{ site.url }}{{site.baseurl}}{{ page.url }}&title={{ page.title }}&summary={{ page.description }}{% endraw %}&source=webjeda```

This is the key to my WebJeda Sharebar.

## How to implement WebJeda share bar?

Create a new ```html``` file inside **_includes** folder and call it **share.html**. Copy paste this code.

{% highlight html %}{% raw %}
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.5.0/css/font-awesome.min.css">


<div class="share-box">
<h5>Share this:</h5>

<a class="f" href="https://www.facebook.com/sharer/sharer.php?u=http://localhost:4000/webjeda-sharebar/" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-facebook-official fa"></i><span> facebook</span></a>

<a class="t" href="https://twitter.com/intent/tweet?text=&url=http://localhost:4000/webjeda-sharebar/" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"><i class="fa fa-twitter fa"></i><span> twitter</span></a>
        
<a class="g" href="https://plus.google.com/share?url=http://localhost:4000/webjeda-sharebar/" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-google-plus fa"></i><span> google</span></a>
        
<a class="r" href="http://www.reddit.com/submit?url=http://localhost:4000/webjeda-sharebar/" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=900,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-reddit fa"></i><span> reddit</span></a>

<a class="l" href="https://www.linkedin.com/shareArticle?mini=true&url=http://localhost:4000/webjeda-sharebar/&title=&summary=&source=webjeda" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-linkedin fa"></i><span> linkedin</span></a>

<a class="e" href="mailto:?subject=&amp;body=Check out this site http://localhost:4000/webjeda-sharebar/"><i class="fa fa-envelope fa"></i><span> email</span></a>                          
</div>
{% endraw %}{% endhighlight %}

I have used icons from **font awesome** which is better than loading icons from local files.

Now copy this line inside your post layout file which will be inside the **_layouts** folder. You have to place this line wherever you want the share bar to appear on your posts.

{% highlight html %}
{% raw %}{% include  share.html %}{% endraw %}
{% endhighlight %}

{% include adsense-inside-post-2.html %}

## Add style to your share bar

I have styled the buttons with the following css. You can change it for your needs.

{% highlight css %}
.share-box a {
  display: inline-block;
  -webkit-box-shadow: 0 0 1px #777;
  box-shadow: 0 0 1px #777;
  padding: 5px 12px;
  margin-right: 5px;
  margin-bottom: 5px;
  text-decoration: none; }
  .share-box a:hover {
    text-decoration: none;
    -webkit-transition: background-color 200ms linear;
    -ms-transition: background-color 200ms linear;
    transition: background-color 200ms linear; }

.f {
  color: #3b5998; }
  .f:hover {
    color: #fff;
    background-color: #3b5998; }

.t {
  color: #4099FF; }
  .t:hover {
    color: #fff;
    background-color: #4099FF; }

.g {
  color: #d34836; }
  .g:hover {
    color: #fff;
    background-color: #d34836; }

.r {
  color: #ff5700; }
  .r:hover {
    color: #fff;
    background-color: #ff5700; }

.l {
  color: #0077b5; }
  .l:hover {
    color: #fff;
    background-color: #0077b5; }

.e {
  color: #444444; }
  .e:hover {
    color: #fff;
    background-color: #444444; }
{% endhighlight %}


Here is how it looks like.

![webjeda share bar for jekyll]({{ site.url }}/images/how-to-add-share-bar-to-jekyll-blog.jpg){: .full}


Here's the demo: [http://webjeda.com/webjeda-sharebar/](http://webjeda.com/webjeda-sharebar/)

Source code: [https://github.com/sharu725/webjeda-sharebar](https://github.com/sharu725/webjeda-sharebar)


## Fontawesome is huge!
Fontawesome takes a lot of time to load because it will be loading all the icons in its CSS. A good way to avoid this loading delay is to optimize fontawesome to load only the icons you need. 

Read: [Optimize Font Awesome to ridiculously low size of 10KB!](https://blog.webjeda.com/optimize-fontawesome/){:target="_blank"}

So this is how you can implement css-only and JavaScript free WebJeda share bar. The onclick attribute is actually JavaScript but I think that doesn't delay the load of share buttons in any manner because it loads only when you click on it. And also it is used only to create a pop up. You can leave that part if you do not want to create a pop up. If you were able to implement this on your blog then please leave a link in the comment.

Thanks for reading!