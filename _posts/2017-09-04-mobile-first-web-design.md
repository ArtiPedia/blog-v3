---
title: Let's Design Mobile First
desc: Mobile First is the best approach for web designing because of ever increasing number of smartphone users. What are the advantages and drawbacks of this approach? Is this the future of web design?
author: sharathdt
tags: Web-Design
image: mobile-first-web-design.png
layout: post
permalink: /mobile-first-web-design/
published: false
sec: 
---

Mobile First Web Design is the new trend in responsive web designing. Unlike covfefe, **mobile first** is a meaningful trend. It is just the reverse approach of what we are generally used to - Desktop First.

Web Designing is almost always done on a desktop(I'm yet to encounter someone who does it on their phone). This was the main reason why we generally design websites for **desktop first** and then use media queries to adapt the site for smaller devices.

* Do not remove this line (it will not be displayed)
{:toc}

This approach has some drawbacks. We get a lot of screen real estate in a desktop to fit in menus, logo, header text, slider, sidebar, widgets etc., When it comes to writing media query for smaller screens, we get stuck at whether to display all those features or not.



## Why Mobile First Web Design? 
Mobile First Web Design is a necessity considering the sheer number of smartphone users.

> More than 2 billion people are using smartphones in {{ page.date | date: '%Y' }}.

A statistical analysis predicts that there will be around 3 billion smartphone users by 2020. That is a huge market. What this statistics imply is that **your content on the internet should be easily consumable through smartphones**.

Google has taken steps to make sure designers give importance to responsive web designing. They did it by adding website's responsiveness as a parameter to rank on their search engine. This one step pushed many website owners to consider responsive web designing.

Google introduced Accelerated Mobile Pages (AMP pages). They are simply pages that load instantaneously and specifically designed for smartphones. Nowadays almost all the media houses are using amp pages.

It also has a [**Mobile Friendly Test**](https://search.google.com/test/mobile-friendly){: target="_blank" rel="nofollow" } that you can use to test whether your website is optimized for smaller screens. Make sure your website passes this test, then submit to Google.

They want to convey that they are serious about smartphone users. Smartphone is a computer that you carry with you all the time and is always on!

Designing a website only for smartphone is actually ok because even desktop users can consume the content. You don't believe me? Then in chrome, open an article on this website and hit **ctrl and +** 5 times. You will see the article exactly how it will show on a smartphone. It is still readable.


## How to use Media Query?
Media Query is basically an if condition used by a browser to determine the screen-width. If satisfactory conditions are met, the CSS inside it will be applied.

Though it seems simple, I had a hard time using it. I needed clarifications on ``max-width`` and ``min-width``. What are they? Why are they called so?

For the first few design projects, I never bothered finding out what they mean. Don't do the same mistake. I have an easy way to remember what they exactly mean.

### Media Query max-width
It means that if the screen width changes below max-width, then the CSS inside it will be applied.

Let's say we have a media query like the following,

{% highlight css %}
@media only screen and (max-width: 600px)  {
        .xyz {
            background-color: blue;
        }
}
{% endhighlight %}


I remember it this way, 

**1. The maximum width of the screen is 600px(Not really but it will be easier to understand).**

**2. If you decrease the width, the CSS inside media query will be applied.**
    
<style>
.xyz {
    height: 200px;
    width: 100%;
    text-align: center;
    padding-top: 50px;
    border: 15px dashed #fff;
    background-color: #0a5;
    font-weight: bold;
    color: #eee;
    
}
.xyz:after {
content: "I'm blue on smartphones :("
}
@media only screen and (max-width: 600px)  {
    .xyz {
        background-color: #05a;
    }
    .xyz:after {
    content: "Blue isn't that bad :)"
}
}
<!-- this is for image border -->
.border {
    border: 1px solid #eee;
}
</style> 
<div class="xyz"></div>
   
    
Consider the box above. It changes color when the size is decreased below 600px. It also changes the content. This can be achieved using ``:after``.



### Media Query min-width
It means that if the screen width changes above the min-width then the CSS defined inside the media query will be applied.

The media query for the box above can be written like this,

{% highlight css %}

.xyz {
    background-color: blue;
}

@media only screen and (min-width: 600px)  {
        .xyz {
            background-color: green;
        }
}
{% endhighlight %}


This will have the same effect as the one with ``max-width``.


I remember it this way,

**1. The minimum width of the screen is 600px(Not really).**

**2. If the screen size increases then the CSS inside media query will be applied.**

I'm not sure if that is what they mean but it helps me understand the Media Query. I used to go refer to media query articles every time I needed to implement them. 


Refer: [w3schools media query](https://www.w3schools.com/css/css_rwd_mediaqueries.asp){: target="_blank" rel="nofollow" }

{% include adsense-inside-post.html %}

## Mobile First Web Design Examples

Here is one such design where the CSS is written for mobile devices first, then media query is written for bigger screens.

`` http://2017.uxlondon.com/ ``

![mobile first web design example](/images/mobile-first-web-design-tutorial.png)

The image depicts the design flow. The header was first designed for mobile, then for tablets and finally for desktops.

Another great example is [Hyde](https://jekyll-themes.com/hyde/){: target="_blank" } by Mark Otto.

This is how it was designed first.

![mobile first web design example](/images/mobile-first-web-design-example-2.png){: .border}

Then it was designed to adjust for bigger screens. When the screen-size increases, the header becomes the sidebar.

![mobile first web design example](/images/mobile-first-web-design-example-3.png){: .border}



## Drawbacks of Mobile First Web Designing
Even though you are using Mobile First approach, you will have to imagine the desktop site first and make your way down to smaller screens. But you have to design the mobile site first and then for tablets and finally for desktops.

It may seem like a small issue but only when you sit down to design a real website you will know the pain. I'm not sure if we can ever avoid this problem.

With majority of browsers supporting [Grid CSS](/css-grid-framework/){: target="_blank"} we can find a hassle free solution. In grid CSS, it becomes easier to place any element anywhere you want in the website.


## Conclusion
A decade ago there were no concerns for designing websites for hand held devices. But now looking at the technological progress, designers should be prepared to change over time. A designer should be ready to adapt to the changes. Designers should be ready to build web interfaces for **smart watches** or **Virtual Reality**. 

