---
layout: default
title: WordPress to Jekyll Migration
desc: Migrating from WordPress to Jekyll is a big hassle. Things should be handled carefully. Learn how to do it here.
permalink: /wordpress-to-jekyll-migration/
adallow: 0
sec: wj
---

<p class="green">Migration from Wordpress to Jekyll tutorial posts will be updated soon.</p>

<div class="homepage">
<div class="mainbox">
    {% assign sorted-posts = site.posts | where: "sec", "wj" %}
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

<style>
.green {

    padding: 20px;
    border-radius:4px;
    color: #fff;
    width: 70%;
    text-align:center; 
    margin: 0 auto;
    background-color: #89dc8b;
    
}
.green a {
    color: #fff;
}
</style>