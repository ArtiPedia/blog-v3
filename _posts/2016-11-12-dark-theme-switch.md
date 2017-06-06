---
title: Night Mode Toggle Across the Website!
desc: Changing background color to a darker one helps reading under low light. This can be achieved easily with JS. But making it to remember the change across the site is a little tricky. Here is a way to do it.
author: sharathdt
tags: Web-Design
image: toggle-night-mode.png
layout: post
permalink: "/dark-theme-switch"
---

I'm not proud of using a smartphone to read articles on the bed. But this is a habit many people have. Reading in low light is bad for your eyes if the phone emits a lot of bright light.

![Dark mode](/images/reading-at-night-on-smartphone-dark-mode.jpg)


There are [apps](https://play.google.com/store/apps/details?id=com.urbandroid.lux&hl=en){: target="_blank" rel="nofollow"} that you can use to reduce the light. A better option is to have a dark theme. Reddit already has this option. Maybe they're aware of their being nocturnal!

* Do not remove this line (it will not be displayed) 
{:toc}

## How to create a dark mode?
When I thought of this problem, I knew JavaScript can do it but [I'm a noob in JS](https://js.webjeda.com){: target="_blank"}. I don't really create my own script. I copy from some pre-existing script and make changes as I like.

But this seemed very easy and I gave it a try to write something on my own which was a horrible code.

{% highlight html %}

<!DOCTYPE html>
<html lang="en">
<head >
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body style="background-color: rgb(255, 255, 255)">
    <p>The button below will switch background color!</p>
    <button onclick="dark()">Switch color</button>
    
    
    <script>
    function dark() {
        if (document.body.style.backgroundColor == 'rgb(255, 255, 255)') {

                document.body.style.backgroundColor = '#333';
        }
        else {
                document.body.style.backgroundColor = 'rgb(255, 255, 255)';
        }
    }
    </script>
    
</body>
</html>

{% endhighlight %}

Copy the code, save as HTML file and open in a browser to see how this works. It is pretty much like the below box.

<div class="dark-div" id="dark-div" style="background-color: rgb(255, 255, 255)" onclick="dark()">
    <p>Click me</p>
</div>


This one works as expected. But I tell you this wasn't easy. First thing is that the JS recognized only RGB code and not HEX. It took me a while to figure that out. It switches background color inline only. Also if you refresh the browser, background color goes back to default.

## Store value across the domain

The problem with this approach is that it is specific to a page. If you switch the theme to dark and navigate to another page in the same domain then it will go back to its normal light theme.

We want it to remember the last switch and keep it across the domain. So if a user switches the theme once then it should remain switched unless he restarts the browser.

Using cookies is one option but it is so yesterday. Europeans know the headache of using cookies on a website. 

A better way is to use either ``localStorage`` or ``sessionStorage``. HTML5 has these options to store up to 5MB of data until you close the browser(sessionStorage) or clear the cache(localStorage). 

After searching through StackOverflow and MDN, I came up with a working code.


## sessionStorage to switch theme

Here is the same box which not only switches its color but also retains it even if you refresh the page!

Try navigating to some other page and come back. This box will still be dark!

<div class="dark-div" id="dark-div-2" style="background-color: rgb(255, 255, 255)" onclick="darker()">
    <p>Switch</p>
</div>
<style>
.dark-div {
    padding:30px 60px; 
    border: 1px dashed #000; 
    width: 300px;
    text-align:center;
    margin: 10px;
    cursor: pointer;

}
</style>

{% include adsense-inside-post.html %}

This uses sessionStorage. If you close the browser and open this link again, you'll see that the box goes back to default background.

I have used this in my new theme [Hagura](http://webjeda.com/hagura/){: target="_blank"}. 


Here is the code I have used to make this happen.

{% highlight javascript %}
document.body.style.backgroundColor = sessionStorage.getItem('bg');
document.body.style.color = sessionStorage.getItem('cc');
function darker() {
     if ( sessionStorage.getItem('bg') === 'rgb(255, 255, 255)') {
         
            sessionStorage.setItem('bg', 'rgb(6, 23, 37)');
            sessionStorage.setItem('cc', '#777');
            
         
     }
    else if (sessionStorage.getItem('bg') == null || undefined) {
        sessionStorage.setItem('bg', 'rgb(6, 23, 37)');
        sessionStorage.setItem('cc', '#777');
        
    }
    else if( sessionStorage.getItem('bg') === 'rgb(6, 23, 37)') {
        
        sessionStorage.setItem('bg', 'rgb(255, 255, 255)');
        sessionStorage.setItem('cc', '#333');
        
  
    }

document.body.style.backgroundColor = sessionStorage.getItem('bg');
document.body.style.color = sessionStorage.getItem('cc');

}

{% endhighlight %}

This for me looks way too long to do such a simple job. But as I told before I'm a novice JavaScript coder. I coded it to get the work done. I think it can be improved. 

**1.** It needs to be simple. If you observe the code, there is a lot of repetitive values which can be minimized.

**2.** <strike>It should not refresh. The changed color will not apply unless the page is refreshed. This is an inconvenience. I hope this can be solved by someone who knows JS.</strike>

I figured it out. Now the color switches without refresh!

## Conclusion
Though it isn't perfect yet, I think it can be used to implement theme switching or any other change that is supposed to happen across the website. 

Let me know if you have successfully implemented this on your website.

Thanks for reading!

<script>function dark(){"rgb(255, 255, 255)"==document.getElementById("dark-div").style.backgroundColor?(document.getElementById("dark-div").style.backgroundColor="rgb(6, 23, 37)",document.getElementById("dark-div").style.color="rgb(255, 255, 255)"):(document.getElementById("dark-div").style.backgroundColor="rgb(255, 255, 255)",document.getElementById("dark-div").style.color="rgb(6, 23, 37)")};</script>
<script>
document.getElementById("dark-div-2").style.backgroundColor=sessionStorage.getItem("bg");document.getElementById("dark-div-2").style.color=sessionStorage.getItem("cc");function darker(){"rgb(255, 255, 255)"===sessionStorage.getItem("bg")?(sessionStorage.setItem("bg","rgb(6, 23, 37)"),sessionStorage.setItem("cc","#777")):null==sessionStorage.getItem("bg")?(sessionStorage.setItem("bg","rgb(6, 23, 37)"),sessionStorage.setItem("cc","#777")):"rgb(6, 23, 37)"===sessionStorage.getItem("bg")&&(sessionStorage.setItem("bg","rgb(255, 255, 255)"),sessionStorage.setItem("cc","#333"));document.getElementById("dark-div-2").style.backgroundColor=sessionStorage.getItem("bg");document.getElementById("dark-div-2").style.color=sessionStorage.getItem("cc")}
;
</script>