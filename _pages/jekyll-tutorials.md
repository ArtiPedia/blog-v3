---
layout: default
title: Jekyll Tutorials
redirect_from: 
    - jekyll-guide/Jekyll
desc: Find all the latest Jekyll Tutorials here along with the steps to implement new features on Jekyll blog or website.
permalink: /jekyll-tutorials/
adallow: 0
---



<div class="homepage">
<div class="mainbox">
    {% assign sorted-posts = site.posts | where: "sec", "tut" %}
     {% for post in sorted-posts  reversed %}
     
    <a class="post-link-index" href="{{ post.url | prepend: site.baseurl }}">
          <div itemscope itemtype="http://schema.org/TechArticle" class="card">
                 <img itemprop="image" alt="{{ post.title }}" class="post-image-index"  src="/thumbs-small/{{ post.image }}" width="300" height="188" />

                <div class="card-footer">
                    <h2 itemprop="headline" class="post-index-title">{{ post.title }}</h2>
                    <hr>
                     <p itemprop="description" class="post-excerpt">{{ post.desc | truncate: 160 }}</p>
               </div>
           
        </div> 
     </a>
          
     
      {% endfor %}
</div>
</div>