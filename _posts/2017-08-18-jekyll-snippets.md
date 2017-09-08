---
title: Jekyll Snippets - Just Copy Paste!
desc: Jekyll Snippets are available in the official website but the styling is not. I'm trying to create jekyll snippets that you can copy it to your jekyll website and it starts working. 
author: sharathdt
tags: 
    - Jekyll 
    - Web-Design
image: jekyll-snippets.png
img-src: "http://www.freepik.com/"
img-src-name: Design by Freepik
layout: post
permalink: /jekyll-snippets/
published: true
sec: tut
---

I will be creating some of the important Jekyll snippets so that they can be directly inserted into a Jekyll website and with no or little editing they start working.

Here - along with the html and liquid code - I have included style as well. Now, it would be easier to implement these snippets. You may have to tinker some values like width, color etc., as per your requiremtnt.

* Do not remove this line (it will not be displayed)
{:toc}


You can always move the style to a different stylesheet or to the head section. But inlining style this way will actually speed up the page load time. But it may not get cached.


## Jekyll Pagination

<script src="https://gist.github.com/sharu725/3c3a3971955d02e24f45edc864bf8172.js"></script>

## Jekyll Contact Form

<script src="https://gist.github.com/sharu725/b8bc09d8a6bb57c637df0b5ae958c155.js"></script>

{% include adsense-inside-post.html %}

## Jekyll Subscribe Form

<script src="https://gist.github.com/sharu725/744bf9357c62a34d416ba71650a64968.js"></script>

## Table of contents
I have designed this so as to look like Wikipedia Table of contents. You can make chages in the style tag to personalize for your website.

<script src="https://gist.github.com/sharu725/2e3b740d14edcd493b623fec5dc1c228.js"></script>

## Disqus Lazy Load
It makes sense to load the Disqus widget only when a user scrolls to the bottom. This code will automatically detect the scrolling and loads Disqus once you reach the bottom of the screen.

<script src="https://gist.github.com/sharu725/ef18ae0645b6b179fcc1263f156f0db9.js"></script>


## Jekyll Social Share Buttons

{% highlight html %}
{% raw %}
/* Call Fontawesome in the head section or in the location where you place the share bar */
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
<style>
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
</style>

<div class="share-box">
<h5>Share this:</h5>

<a class="f" href="https://www.facebook.com/sharer/sharer.php?u={{ site.url }}{{site.baseurl}}{{ page.url }}" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-facebook-official fa"></i><span> facebook</span></a>

<a class="t" href="https://twitter.com/intent/tweet?text={{ page.title }}&url={{ site.url }}{{site.baseurl}}{{ page.url }}" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"><i class="fa fa-twitter fa"></i><span> twitter</span></a>
        
<a class="g" href="https://plus.google.com/share?url={{ site.url }}{{site.baseurl}}{{ page.url }}" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-google-plus fa"></i><span> google</span></a>
        
<a class="r" href="http://www.reddit.com/submit?url={{ site.url }}{{site.baseurl}}{{ page.url }}" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=900,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-reddit fa"></i><span> reddit</span></a>

<a class="l" href="https://www.linkedin.com/shareArticle?mini=true&url={{ site.url }}{{site.baseurl}}{{ page.url }}&title={{ page.title }}&summary={{ page.desc }}&source=webjeda" onclick="window.open(this.href, 'mywin',
'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" ><i class="fa fa-linkedin fa"></i><span> linkedin</span></a>

<a class="e" href="mailto:?subject={{ page.title }}&amp;body=Check out this site {{ site.url }}{{site.baseurl}}{{ page.url }}"><i class="fa fa-envelope fa"></i><span> email</span></a>                          
</div>
{% endraw %}
{% endhighlight %}

Read - [Webjeda Sharebar](http://webjeda.com/webjeda-sharebar/){: target="_blank"}

Fontawesome is a huge css file. [Optimize fontawesome](/optimize-fontawesome/){: target="_blank"} to speed up page load time.


<style>
h2 {
    margin-top: 2em;
}
</style>


{% include adsense-inside-post-2.html %}

## Reading Time

<script src="https://gist.github.com/sharu725/d8c9566562166d6d1fd6f3f49972245e.js"></script>


To be continued...