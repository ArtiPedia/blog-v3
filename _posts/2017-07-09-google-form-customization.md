---
title: Google Form Customization for Static Websites!
desc: Google Form customization is done to remove the branding that is present at the end of Google Forms. This way we can have our own style for a form. We can also use these forms on static websites!
author: sharathdt
tags: Web-Design
image: customize-google-forms.png
img-src: "http://www.freepik.com/"
img-src-name: Design by Freepik
layout: post
permalink: /google-form-customize/
---

Customizing Google Forms is important for someone who trusts Google but doesn't like their branding at the bottom of the forms. Google offers two ways of using their form. One is embedding the form on our website and the second is redirecting users to the form page.

* Do not remove this line (it will not be displayed) 
{:toc}

Both the methods are not that great because you have to choose the template Google provides you and you have to bear the Google branding at the bottom.

![Customize Google Forms](/images/google-form-customization-1.png)

This is what I'm talking about. Many of us may not bother about the branding. A real headache is when you embed the form on your website, it may display its own scrollbar and may look totally different from your website's color scheme.

## Create a Google form
Go to [Google Forms](https://docs.google.com/forms/u/0/){: target="_blank"} and create a form with values **Name** and **Email**. I'm keeping it simple for this tutorial. The next part is to customize Google form.

![Customize Google Forms](/images/google-form-customization-2.png)

## Customize Google Form 
We are going to scrape this Google form for certain values and implement it in our own form. So the first step is to create a form. 

You can have any field in the contact form but I will be using only **name** and **email**. Once you create the form, click on **Send** and it will show you how you can implement the form.

Get the form link and open it in a new tab. It is easier if you're using a Chrome browser. Now, inspect(f12) each and every field in the form and find **name** attribute. Copy whatever the value present in it. It will be like ``entry.742532386``.

Find ``<form>`` tag and copy the URL found in **action** attribute.

{% include adsense-inside-post.html %}

![Customize Google Forms](/images/google-form-customization-3.png)

## Create a similar form

Create your own barebone form with the same fields as in the Google form. For this example, a sample form will look like this.

{% highlight html %}
<form class="form" action="">
    
      <label>Name</label>
      <input name="name" type="text" />

      <label>Email</label>
      <input name="email" type="email" required />

      <input type="submit" value="Send" />

</form>
{% endhighlight %}

## Change Action and Name values

Now in your barebone form, change the action to whatever the action you find in the Google form inspection. It will look something like this ``https://docs.google.com/forms/d/e/1FAIpQLSdqGYth5-G2cP8SILJwjOcJ38vit-Rv8E9SXmtnJUu4ifMcGw/formResponse``.

Copy this value and paste it in your form's action. Also, copy respective **name** values and put it in appropriate fields. The completed form should look like this.

{% highlight html %}
<form class="form" action="https://docs.google.com/forms/d/e/1AFIpQLSdqYGth5-G2cP8SILJwjOcJ38vit-Rv8E9SXmtnJUu4ifMcGw/formResponse">
   
      <label>Name</label>
      <input name="entry.742532386" type="text" />
      
      <label>Email</label>
      <input name="entry.1558941179" type="email" required />


      <input type="submit" value="Send" />

</form>
{% endhighlight %}

## Publish it on any website
The good thing about the form is that it not only works but it works on static websites as well. This is a great way to insert Google forms in Jekyll websites and blogs hosted on Github Pages.

Here is a working form that you can check. I have restricted the entries to 12 characters so as to avoid long spams.


<script type="text/javascript">var submitted=false;</script>
<iframe name="hidden_iframe" id="hidden_iframe" style="display:none;"     
onload="if(submitted) {window.location='{{site.url}}{{page.url}}';}"></iframe>
<form action="https://docs.google.com/forms/d/e/1FAIpQLSdqGYth5-G2cP8SILJwjOcJ38vit-Rv8E9SXmtnJUu4ifMcGw/formResponse" method="post" target="hidden_iframe" 
onsubmit="submitted=true;">
      <label>Name</label>
      <input name="entry.742532386" type="text" maxlength="10" placeholder="Max 12 characters" />
      <br>
      <label>Email</label>
      <input name="entry.1558941179" type="email" required maxlength="10" placeholder="Max 12 characters"/>
      <br>
      <input type="submit" value="Send" />

</form>


Style this form however you want to but I'm keeping it simple without any styles applied.


## Get responses in a Google SpreadSheet
This is a cool feature where you can get the entries in a spreadsheet! In the form, click on **Responses** tab. You should be able to see all the responses right there. But you will see a spreadsheet icon at the top right corner. Click on it and it will ask you whether you'd like to save responses in a new spreadsheet. Click **Create**


![Customize Google Forms](/images/google-form-customization-4.png)


Once you create it, you should see a spreadsheet created with tabs for **Name** and **Email**.


![Customize Google Forms](/images/google-form-customization-6.png)


## Google Form Redirection

After form submission, you will be redirected to a Google page where it says response is received. You can edit the message and provide a link back to the website. This custom message and link will be shown to the users after they submit the form.

![Customize Google Forms](/images/google-form-customization-5.png)

But if you don't want it to be redirected back to your page, then please use this code instead.

{% highlight html %}

 <script type="text/javascript">var submitted=false;</script>
 <iframe name="hidden_iframe" id="hidden_iframe" style="display:none;" onload="if(submitted)  {window.location='THE REDIRECT LINK HERE';}"></iframe>
 
<form action="FORMACTION CODE HERE" method="post" target="hidden_iframe" 
onsubmit="submitted=true;">
      <label>Name</label>
      <input name="ENTRY HERE" type="text" placeholder="Name" />
      <br>
      <label>Email</label>
      <input name="ENTRY HERE" type="email" placeholder="Email"/>
      <br>
      <input type="submit" value="Send" />

</form>

{% endhighlight %}

## Google Form Notification
Another cool feature is to get notifications to your email upon every entry. You can activate this feature in the spreadsheet by going to **Tools >> Notification Rules...**. Set rules on when to receive notifications and you're good to go.

![Customize Google Forms](/images/google-form-customization-7.png)


## Check if the Google Form is working
In the form that I have inserted [here](#publish-it-on-any-website) is a working form and you can see the entries [here](https://docs.google.com/spreadsheets/d/1_vt8il8LpxEi8_DmX0yxxRambpw700cdMC2yMIGWqbk/edit?usp=sharing){: target="_blank"}.

{% include adsense-inside-post-2.html %}

Try not to spam
{: .r}

## Conclusion
Though there are other free services like [Formspree](https://blog.webjeda.com/jekyll-contact-form/){: target="_blank"}, [SimpleForm](https://blog.webjeda.com/jekyll-subscribe-form/){: target="_blank"} etc, I trust Google with my data. This is because I'm aware that Google uses it for targeting ads. But I don't know what other services use the data for. While using SimpleForm, I used to get a lot of spam from digital marketers. Obviously, the guy who owns SimpleForm is selling the email addresses to someone. 

I don't mind it because I'm using the service for free. But I'm concerned about the entries by my users. I'm pretty sure that their emails will also be collected and sold. I don't want my users' inboxes to be cluttered with spam. At least with Google Forms, I did not face that issue. 

Try this and let me know - in the comment section - if it has worked for you. Any suggestions to improve the article is welcome. 
