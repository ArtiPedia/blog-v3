---
layout: default
title: Jekyll Themes
desc: Webjeda jekyll themes is a showcase of hand-picked, responsive jekyll themes. You will find some of the best jekyll themes that can be used for your website blog or portfolio.
permalink: /jekyll-themes/
---

<p class="green">I will be moving all the themes to <a href="https://jekyll-themes.com"><strong>jekyll-themes.com</strong></a> soon.</p>

<h1 style="text-align:center">Jekyll Themes</h1>
<div class="mainbox">
   
 {% for jekyll-themes in site.jekyll-themes reversed  %}
   <a class="post-link-index" href="{{ jekyll-themes.url | prepend: site.baseurl }}">
      <div class="card" itemscope itemtype="http://schema.org/TechArticle">
            <img alt="{{ jekyll-themes.title }}" class="post-image-index" itemprop="thumbnailUrl" src="/thumbs/{{ jekyll-themes.image }}" width="300" height="188" />
            <div class="card-footer">
              <h2 itemprop="headline" class="post-index-title">{{ jekyll-themes.title }}</h2>
                    <hr>
                     <p itemprop="description" class="post-excerpt">{{ jekyll-themes.desc | truncate: 160 }}</p>
           </div>

    </div> 
 </a>
  {% endfor %}   
</div>
<style>
.green {
padding: 20px;
border-radius:4px;
color: #fff;
width: 80%;
text-align:center; 
margin: 0 auto;
background-color: #89dc8b;  
}
.green a {
    color: #fff;
}
</style>