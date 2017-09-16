---
title: Search
layout: page
desc: Search webjeda website for Jekyll tutorials and github tutorials from here. 
permalink: /search/
---

<style>
main {
    max-width: 1100px !important;
}

#search-container {
    min-height: 600px;
    width: 100%;
}

.search {
    position: relative;
    margin: 0 auto;
    width: 600px;
}
#i-search {
    position: absolute;
    z-index: 999;
    top: 14px;
    right: 14px;
    stroke: #aaa
}

#result-container li {
    line-height: 2.2
}
a.post-link-index, a.post-link-index:hover  {
    border: none;
}
input[type=text] {
    width: 100%;
    outline: 0;
    padding: 15px 25px;
    margin: 5px 1px 3px 0;
    border: none;
    border-radius: 1px;
    box-shadow: 0 1px 0 0 rgba(0, 0, 0, .16), 0 0 0 1px rgba(0, 0, 0, .08)
}

input[type=text]:focus,
input[type=text]:hover {
    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .16), 0 0 0 1px rgba(0, 0, 0, .08);
    margin: 5px 1px 3px 0;
    padding: 15px 25px;
    border: none;
    outline: 0;
    -webkit-transition: all .3s ease-in-out;
    -moz-transition: all .3s ease-in-out;
    -ms-transition: all .3s ease-in-out;
    -o-transition: all .3s ease-in-out
}

@media screen and (max-width:600px) {
    #search-container {
        width: 100%;
        margin: 1em auto
    }
    input[type=text] {
        width: 100%;
        box-sizing: border-box
    }
}</style>

<!-- Html Elements for Search -->
<div id="search-container">
<div class="search">
<input type="text" id="search-input" placeholder="" autofocus><svg id="i-search" viewBox="0 0 32 32" width="26" height="26" fill="none" stroke="currentcolor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><circle cx="14" cy="14" r="12" /><path d="M23 23 L30 30"  /></svg>
</div>
<div id="results-container" class="mainbox"></div>
</div>

<!-- Script pointing to search-script.js -->
<script src="/js/jekyll-search.min.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  searchResultTemplate: '<a class="post-link-index" href="{url}"><div itemscope itemtype="http://schema.org/TechArticle" class="card"><span class="image"><img itemprop="image" alt="{title}" class="post-image-index" src="{image}" width="300" height="188" /></span><div class="card-footer"><h2 itemprop="headline" class="post-index-title">{title}</h2><hr><p itemprop="description" class="post-excerpt">{description}</p></div></div></a>',
  json: '/search.json'
})
</script>

