---
title: Adding Top Progress Bar to Websites
desc: Top bars are beautiful looking lines at the top of a website. A colored top bar would not do any harm. Instead, it increases the beauty of your website (if used correctly). Read to know how I have implemented it in my websites.
keywords: top bar, website top line, top border of website, top colored line in websites
author: sharathdt
tags: Web-Design Github-Pages 
image: top-bar-on-websites.png
layout: post
permalink: /top-bar-website/
---


<script src="/demo/nanobar.min.js"></script>
<script>
var options = {
	classname: 'my-class',
    id: 'my-id'
};
var nanobar = new Nanobar( options );
nanobar.go( 30 );
nanobar.go( 76 );
nanobar.go(100);
</script>
<style>
.bar{
  background:#f04c78;
}
</style>


## Why top bar?
{: .clear}
I started considering top bar only after I saw that the designers from [Quora](https://www.quora.com/){:rel='nofollow'}{:target="_blank"} started using it(now they are not!). I also used to have a top bar on this blog but after the new design I no longer use it. But, one of my blogs [Nallikayi](http://nallikayi.com){:target="_blank"} has a nice top bar which goes with the design.



* Do not remove this line (it will not be displayed) 
{:toc}

I remember YouTube using a red top bar to show how the progress of page loading. You can see it when you click on a video link. Actually it is a great idea to show the users how much page has been loaded without any distractions. By the time I'm writing this blog <a rel="nofollow" href="https://www.freecharge.in" alt="Freecharge">Freecharge</a> is using the top bar as a progress indicator. It must be a ```div``` on top with a 1 pixel border but looks like body top border.

{% include adsense-inside-post.html %}

![Android chrome browser top loading bar]({{ site.url }}/images/android-chrome-browser-using-top-bar-screenshot.jpg)
{: .right .half}

If you have seen Chrome browser on android, they still use this. May be it is using a different code but visually similar to that we use in websites.

So here it is giving some valuable information. But what I want is just a minimal colored top bar to enhance the visual appearance. It is very easy and can be done with a single line of code!
{: .clear}


## Top Progress Bar

### Did you observe a red top bar on this page?
If you did not then hit refresh. This page shows page loading preogress as a top bar.  This gives users an idea of whether the page has fully loaded or not. The code pretty small and no jQuery required.

### How to implement progress top bar?

#### Download nanobar
[Nanobar](http://nanobar.jacoborus.codes/){:rel='nofollow'}{:target="_blank"} is javascript wich generates a highly customizable top bar. I will show the basic top bar implementation.

Download the [minified version](https://github.com/jacoborus/nanobar/archive/master.zip){:target="_blank"} here.

#### Generate top bar
Before we generate one, we have to call the javascript that we just downloaded. Copy the ``nanobar.min.js`` file your project or website folder(may be inside /js folder).

Now call it using a script tag. If you are using Jekyll and you want top bar to show page load progress on all the pages, then do these steps on ``default.html`` or the default layout.

{% highlight html %}
<script src="/demo/nanobar.min.js"></script>
{% endhighlight %}

#### Give it a class and id(optional)
If you want to change the looks of the bar then you should give it a class or id. Here is how we can do it. We are also generating a new Nanobar with some options which define the length of the bar.

{% highlight html %}
<script>
var options = {
	classname: 'my-class',
    id: 'my-id'
};
var nanobar = new Nanobar( options );
nanobar.go( 30 );
nanobar.go( 76 );
nanobar.go(100);
</script>
{% endhighlight %}

#### Customize your Top Progress Bar
Give top progress bar a color that suits the scheme of your website. It is better to give it a contrasting dark color in order to highlight the bar.

{% highlight html %}
<style>
.my-class .bar {
  background:#f04c78;
}
</style>
{% endhighlight %}

#### Output Top Bar
The output html of the top bar looks like this. So you can always customize ``.bar`` class inside ``.my-class`` to give it a color, increase the height etc...

{% highlight html %}
<div class="nanobar my-class" id="my-id" style="position: fixed;">
    <div class="bar"></div>
</div>
{% endhighlight %}



## Simple Top bar

### what is the code for Top Bar?

If you are looking for a top bar which is static, then just copy these lines to your css file and you'll have a top bar! So far we have called this top bar but in reality it is the top border of your body. Normally it is invisible, we are just giving it a size, style and color. Pretty neat. Isn't it? There is not a single extra ```div``` used. So there is no extra load on your website!


{% highlight css %}
body {
  border-top: 4px solid #37ba8a;
  margin: 0;
}
{% endhighlight %}


So that's all there is! Use ```em``` instead of ```px``` if you like. I use ```em``` as I have configured it to adjust to the screen-size.  Now change the color according to your theme and don't make it very contrasting, say a blue top bar on red background. That is not very pleasing to eyes. And also make sure the body has no margin. Otherwise you may not get the top bar where you wanted.

Though it is a simple thing, it gives a huge impact on the look and aesthetics.


## Extensible!
![top border used by google]({{ site.url }}/images/top-border-used-by-gmail.jpg)
{: .right .half}
This can be used on buttons to make them look awesome! This can give a modern look to almost all the elements. One such thing I have noticed is in **gmail** categories.

Here is a button with just borders
{: .clear}

<button class="border-style">WebJeda</button>

<style>
.border-style {
    font-size: 18px;
    color: #41A720;
    margin: 0;
    padding: 10px 25px 10px 25px;
    background-color: transparent;
    border: 1px solid #41A720;
    border-radius: 2px;
}
</style>

Here is the HTML code..

{% highlight html %}
<button class="border-style">WebJeda</button>
{% endhighlight %}

.. and CSS

{% highlight css %}
button.border-style {
    font-size: 18px;
    color: #41A720;
    margin: 0;
    padding: 10px 25px 10px 25px;
    background-color: transparent;
    border: 1px solid #41A720;
    border-radius: 2px;
}
{% endhighlight %}

Try mplementing top bar on your website and let me know how it went.

And don't forget to leave the link in the comment section, of your website with newly created top bar.

Thanks for reading!


