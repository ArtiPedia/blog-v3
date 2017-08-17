---
layout: default
title: Jekyll Video Tutorials
desc: Jekyll Tutorial Videos are available here. See how I do Jekyll.
permalink: /videos/
adallow: 0
videos:
    - id: bwThn0rxv7M
      title: How to create a website on Github Pages?
      desc: Sorry for the quality of this video. This one is my first video.

    - id: GJCzy6hYTLQ
      title: Free and Easy Web Hosting Using Github!
      desc: Learn how to create and host a website on Github and host it for free using Github Pages. 
       
    - id: hUChaN-VRIc
      title: How to add a custom domain in Github Pages?
      desc: In this video, I'm configuring custom URL to my website which is hosted on Github Pages. 
      
    - id: U0idtvxVo9I
      title: How to create Jekyll blog?
      desc: In this video, I'm creating a beautiful Jekyll blog on Github Pages.
      
    - id: gI-FcrkDveA
      title: How Jekyll Works?
      desc: Jekyll is really simple once you know how it works. You can make your blog do wonders once you know how to play with templates, layouts, loops and curly braces.     

    - id: Ff8_V6IIbw0
      title: How to Create and List Jekyll Posts
      desc:  In this video I have talked about Jekyll Posts. How to create new posts, how to index them in homepage.

    - id: IP6HsgwQkvs
      title: Create a working contact form in Jekyll
      desc: In this video I will be showing how to create forms in static websites like Github pages or Jekyll blogs. 
               
      
    - id: zhHY4tWpFz4
      title: Subscribe form for Jekyll
      desc: Subscribe form for Jekyll is not readily available because forms usually work with php code to send emails. But with this method, we can add a subscribe form on any Jekyll blog which will work out of the box.
           
    - id: bty7LHm14CA
      title: How to Install Jekyll Themes? 
      desc: Learn how to use a Jekyll Theme for your website, blog or prtfolio. I will be discussing some of the common issues that we face while installing and also how to resolve them.

                 
    - id: T2nx6tj-ZH4
      title: Minimal Jekyll Theme Thunder
      desc: Thunder is a lightning fast responsive theme based on default Jekyll theme. It is minimal and free from JavaScript. It has a css file of size 5kb.
        
                 
    - id: 0PxSYhrHRS0
      title: Using Markdown in Jekyll
      desc: Jekyll is really simple once you know how it works. You can make your blog do wonders once you know how to play with templates, layouts, loops and curly braces.   
      
    - id: q0OP81HDQzE
      title: Using Liquid Syntax in Jekyll
      desc: Jekyll is really simple once you know how it works. You can make your blog do wonders once you know how to play with templates, layouts, loops and curly braces.       

---

<div class="homepage">
<div id="mainbox">
{% for video in page.videos %}
 <a target="_blank" href="https://www.youtube.com/watch?v={{video.id}}">
        <div class="card">
        <div class="youtube-embed" style="background-image: url(https://i.ytimg.com/vi/{{video.id}}/hqdefault.jpg); position: relative"><div class="play"></div></div>
            <div class="card-footer">
                <h2 itemprop="headline" class="post-index-title">{{video.title}}</h2>
                <hr>
                 <p itemprop="description" class="post-excerpt">{{ video.desc | truncate: 160 }}</p>
            </div>
            
            
            
        </div> 
</a>
{% endfor %}
</div>
</div>

