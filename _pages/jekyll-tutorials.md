---
layout: default
title: Jekyll Tutorials
desc: 
permalink: /jekyll-tutorials/
adallow: 0
---



<div class="homepage">
<div id="mainbox">
    {% assign sorted-posts = site.posts | where: "sec", "tut" %}
     {% for post in sorted-posts  reversed %}
     
    <a class="post-link-index" href="{{ post.url | prepend: site.baseurl }}">
          <div itemscope itemtype="http://schema.org/TechArticle" class="card">
                 <img alt="{{ post.title }}" class="post-image-index" itemprop="thumbnailUrl" src="/thumbs-small/{{ post.image }}" width="300" height="188" />

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