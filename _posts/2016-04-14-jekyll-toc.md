---
title: Jekyll Table of Contents - Wikipedia Look!
desc: Table of contents on Jekyll is easy to implement. TOC provides a quick look at what the article is all about. Also, users can skip to any topic they like just by clicking on it. Learn how to add Table of Contents (TOC) to your Jekyll blog.
keywords: jekyll toc
author: sharathdt
tags: Jekyll  
image: jekyll-toc.png
permalink: /jekyll-toc/
layout: post
---


## Why Table of Contents?
I always liked the Wikipedia **Table of Contents** section which is present in almost every article. It gives a good insight to the whole article with headlines. Imagine, if that was not there; how hard it would be to find things that we are specifically looking for. Things like someone's career, early life etc., Here is a [sample page](https://en.wikipedia.org/wiki/Kannada){:rel='nofollow'}{:target="_blank"} wikipedia page.

I have used a similar kind of TOC on my blog(at least it looks similar!). So here is the Table of Contents of this blog post.


* Do not remove this line (it will not be displayed) 
{:toc}



Table of Contents for Jekyll blog or any blog for that matter is not really necessary if the article is very short. But, for a long detailed article, a TOC section provides a good insight and helps skipping to the desired topic.

{: .clear}

## How to add TOC for Jekyll posts?

There are [plugins](https://jekyllrb.com/docs/plugins/){:rel='nofollow'}{:target="_blank"} for Jekyll to generate TOC but, I have stayed away from them for one reason - I want the complete control on my website. 

When I was using WordPress, there was a simple plugin called TOC and it worked like charm. It also had some color schemes available for it. But when we are dealing with Jekyll, plugins are very new and can be unstable. I'm not against Jekyll plugins or something but I'm just waiting for them to be simple to use. 

Now, let's dive in and install TOC.


If you are using kramdown as your markdown processor then you can add the following lines anywhere on the post to add a TOC. Which is pretty simple if you do not want to use JavaScript on your blog 
{% highlight md %}
* Do not remove this line (it will not be displayed)
{:toc}
{% endhighlight %}
You can make it look pretty by adding this style

{% highlight css %}

// Adding 'Contents' headline to the TOC
#markdown-toc::before {
    content: "Contents";
    font-weight: bold;
}


// Using numbers instead of bullets for listing
#markdown-toc ul {
    list-style: decimal;
}

#markdown-toc {
    border: 1px solid #aaa;
    padding: 1.5em;
    list-style: decimal;
    display: inline-block;
}

{% endhighlight %}


For this to work you should be using kramdown as your markdown preprocessor. Mention this in the ``_congif.yml`` file and restart the server to make it work.

{% highlight yml %}

markdown: kramdown

{% endhighlight %}

But if this doesn't work for you then you can follow the procedure below.


### Step 1: Download necessary files

**Download the zip file:** [jekyll-table-of-contents](https://github.com/ghiculescu/jekyll-table-of-contents/archive/master.zip){:rel='nofollow'}{:target="_blank"}. Thanks to [Alex Ghiculescu](https://github.com/ghiculescu){:rel='nofollow'}{:target="_blank"} for this repository. Don't forget to give a star to this repository if it works for you.

So the repository you just downloaded has a single JavaScript file ```toc.js``` which is enough for creating Table of Contents.

### Step 2: Install the script in Jekyll repository

Place the ```toc.js``` inside your repository somewhere. Maybe inside a folder called **js** where all your scripts are placed.

Now call this JavaScript file where you want the TOC to show up. Usually, all the posts require TOC. So you can call it in the **post layout**. If you want it to be shown on pages then call it on **page layout**. And if you want it everywhere then it is wise to call the file in the **default layout**.

Add this line of code in the layout file you would like the TOC to appear. 
{% highlight html %}
<sript src="/path/to/toc.js"></sript>
{% endhighlight %}

I'm using it only on my posts. So I'm calling it only on the posts layout. This is how it looks like

{% highlight html %}{% raw %}
---
layout: default
---

<article class="post">
  <h1 class="post-title">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  {{ content }}
</article>

<sript src="/path/to/toc.js"></sript>

{% endraw %}{% endhighlight %}

{% include adsense-inside-post.html %}

### Step 3: Call TOC in the layout.

I personally like calling it in particular places of my articles. So I go into all my posts and paste the below line in certain places. So if you look at my posts, the Table of Contents does not belong to one fixed place. It can be in the first paragraph or second paragraph and so on.

But this is a tedious task if you have a lot of posts. It is better to place the code in the layout itself than individual posts.

Use this line of code in the layout and the TOC will load there.

{% highlight html %}
<div id="toc"></div>
{% endhighlight %}

I'm calling it in my post layout; just above the content.

{% highlight html %}{% raw %}
---
layout: default
---

<article class="post">
  <h1 class="post-title note info">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  <div id="toc"></div>
  {{ content }}
</article>

<sript src="/path/to/toc.js"></sript>

{% endraw %}{% endhighlight %}


### Step 4: Initiate TOC

Before initiating Table of Contents, it is logical to wait till all the contents are loaded. Because TOC uses all the headers and it is necessary that all the headers are loaded before the initiation of TOC. So to the post layout, add this snippet of code that waits till the page is completely loaded.

{% highlight html %}
<script type="text/javascript">
$(document).ready(function() {
    $('#toc').toc();
});
</script>
{% endhighlight %}

Here is the complete **post layout** that is ready to load Table of Contents on your Jekyll posts.

{% highlight html %}{% raw %}
---
layout: default
---

<article class="post">
  <h1 class="post-title note info">{{ page.title }}</h1>
  <time datetime="{{ page.date | date_to_xmlschema }}" class="post-date">{{ page.date | date_to_string }}</time>
  <div id="toc"></div>
  {{ content }}
</article>

<sript src="/path/to/toc.js"></sript>

<script type="text/javascript">
$(document).ready(function() {
    $('#toc').toc();
});
</script>

{% endraw %}{% endhighlight %}



This code will call the TOC function once the DOM is ready. After rendering, this is how it will look like

<svg xmlns="http://www.w3.org/2000/svg" width="386" height="196" viewBox="34.9 -95.5 385.5 195.5" font-family="'Helvetica'" font-size="16" fill="#1283D8"><text transform="matrix(1 0 0 1 70.6577 -44.593)">  1. </text><text transform="matrix(1 0 0 1 87.0229 -44.593)">  Why Table of Contents?</text><text transform="matrix(1 0 0 1 70.6353 -23.0833)">  2. </text><text transform="matrix(1 0 0 1 88.0464 -23.0833)">  How to add TOC for Jekyll posts?</text><text transform="matrix(1 0 0 1 107.4556 -1.5745)">   1. </text><text transform="matrix(1 0 0 1 123.894 -1.5745)">  Step 1: Download necessary files</text><text transform="matrix(1 0 0 1 107.4556 19.9353)">   2. </text><text transform="matrix(1 0 0 1 123.894 19.9353)">  Step 2: Install the script in Jekyll repo</text><text transform="matrix(1 0 0 1 107.4556 41.4431)">   3. </text><text transform="matrix(1 0 0 1 123.894 41.4431)">  Step 3: Call TOC in the layout.</text><text transform="matrix(1 0 0 1 107.4556 62.9509)">   4. </text><text transform="matrix(1 0 0 1 123.894 62.9509)">  Step 4: Initiate TOC</text><text transform="matrix(1 0 0 1 107.4556 84.4607)">   5. </text><text transform="matrix(1 0 0 1 123.894 84.4607)">  Step 5: Configuration</text><text transform="matrix(1 0 0 1 70.6353 -69.7454)" font-family="'Helvetica'" font-size="19" style="fill:#333;font-weight:bold">  Contents</text><rect x="34.9" y="-95.5" width="385.5" height="195.5" style="fill:none;stroke:#3D3D3D"/></svg>

{: .right .half}
It may not look the same when you first set up TOC but I will give you the styling that I have used for this one which looks like Wikipedia TOC.

{% highlight css %}
div#toc {
    padding: 10px;
    border: 1px solid #aaa;
    display: inline-block !important;
}
{% endhighlight %}
{: .clear}

And also the word **Contents** was actually **Jump to. .** by default. You can change this in the JavaScript file ```toc.js``` between ```<i>``` tag.

{% highlight css %}
title: '<i>Jump to...</i>';
{% endhighlight %}

For some reason, the TOC section assumes the style ```display: block``` which will cover the whole page. But I wanted it on one side of the page. So I have added the code ```display: inline-block!important```. I personally do not like using **!important** but here I had to.


{% include adsense-inside-post-2.html %}


Now, different markdown handlers process markdown differently. Table of Contents will create an anchor tag for every headline. But this is not supported by all the markdown processors. **Kramdown** is good with it but if you are using **redcarpet** or **rdiscount** you have to make some changes in the **_config.yml** file.


I suggest you change the markdown processor to **kramdown** as it is the [only supported markdown engine](https://github.com/blog/2100-github-pages-now-faster-and-simpler-with-jekyll-3-0){: target="_blank"}{: rel="nofollow"} by github pages.
{: .y}


**redcarpet**
{% highlight css %}
markdown: redcarpet
redcarpet:
    extensions: [with_toc_data]
{% endhighlight %}


**rdiscount**
{% highlight css %}
markdown: rdiscount
rdiscount:
    extensions:
      - generate_toc
{% endhighlight %}


### Step 5: Configuration
{: .clear}
Table of Contents by default will consider all the headers h1, h2, h3, h4, h5 and h6.

What if you don't want any h4 or h5 displayed? Use this code in place of the one we used in [Step 4](#step-4-initiate-toc).

{% highlight js %}
$('#toc').toc({ headers: 'h1, h2, h3, h6' });
{% endhighlight %}

This code will ensure that only the mentioned headers will be considered for TOC. There are also other things that you can change. If you want to know all the configurations then please visit [this repository](https://github.com/ghiculescu/jekyll-table-of-contents){:rel='nofollow'}{:target="_blank"} and go through instructions given.

I hope that helped you set up TOC on your website. Ask any doubts you have through comments.

Thanks for reading!