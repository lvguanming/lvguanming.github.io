---
layout: post
published: true
title: "Jekyll Estimated Reading Time: Liquid, no plugins"
mathjax: false
featured: false
comments: true
chart: false
description: Implementing Medium inspired Estimated Reading Time (ERT) Calculator on Github Pages with Jekyll
categories: 
  - webdevelopment
tags: jekyll reading time
---

The first time I discovered Medium, I fell in love with its Estimated Reading Time (ERT) feature. It helps bring in the right audience to the right article. The idea behind of this is, maybe it’s early in the morning, you’re in the mood of reading something terse while you get prepared for work, and at dawn, you’re back at home and you just want to curl up on the couch and gorge in a long essay. The ERT helps you find the right article, for the right time.

![Medium ERT]({{ site.url }}/images/post/medium-readingtime.jpg "Medium Estimated Reading Time")

So with that in mind, I looked on the internet if someone has already made a code-snippet for this. Sure enough, I found a Jekyll plugin that does it right. Have a look at this [Jekyll Estimated Reading Times Plugin](http://51bits.com/writing/estimated-reading-times-in-jekyll/) by 51bits. But the problem was, I was and currently am hosting with GitHub pages, which does not allow external plugins. So I wrote my own code in Liquid.

First of all, lets make a switch for the Estimated Reading Time feature, so that you can turn on/off the feature anytime you like. Put these two lines in your `_config.yml` file.

{% highlight yaml %}
# Read Time is a calculator to provide post Estimated Reading Time (ERT) based on word count. Usage is recommended.
readtime:		true
wpm:			200
{% endhighlight %}

`readtime` acts as a switch to turn on/off the ERT feature sitewide. `wpm` is used for specifying the *average words-per-minute* your viewers can read.

Then the calculator for the blog index page:

{% highlight ruby %}
{% raw %}
  {% if site.readtime %}
  {% for post in site.posts %}
  	{% assign readtime = post.content | strip_html | number_of_words | append: '.0' | divided_by:site.wpm %}
  {% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

Without `append: '.0'`, you will get a whole number, but it will not be rounded. So 4.8 will be 4, not 5. Liquid provides math operators which can round numbers, but with the update of Jekyll version 2.2.0, those operators has been deprecated in favor of more elegant *data-type* based calculations.

The calculator does not display anything on your page, it just calculates the reading times for each post in your blog and holds it in the RAM. Place the code anywhere before you call `{% raw %}{{ readtime }}{% endraw %}` in the page to actually display the calculated results.

But before displaying the data lets make the code better. Lets give the calculator a fallback option if you did not specify or forgot to specify a wpm value in the `_config.yml` file. I opt to use 180 wpm as the default fallback option. But you can use whatever you like.

{% highlight ruby %}
{% raw %}
{% if site.readtime %}
  {% for post in site.posts %}
    {% if site.wpm %}
      {% assign readtime = post.content | strip_html | number_of_words | append: '.0' | divided_by:site.wpm %}
    {% else %}
      {% assign readtime = post.content | strip_html | number_of_words | append: '.0' | divided_by:180 %}
    {% endif %}
  {% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}

Now we come to the main part, displaying the Estimated Reading Time (ERT) for each post.

Simply putting the `{% raw %}{{ readtime }}{% endraw %} minute` tag will display a floating point value.

{% assign readtime = page.content | strip_html | number_of_words | append: '.0' | divided_by:site.wpm %}
For this post `{% raw %}{{ readtime }}{% endraw %} minute` will display `{{ readtime }} minute`

But I am sure you are more interested in integer values for aesthetic and ease of reading purposes. With the Jekyll 2.2.0 update, Jekyll supports a wide array of important data types like `int` and `float` and does not support many of the older liquid math operators that would have made doing this much easier, which is good in a sense. Prior to Jekyll version 2.2.0, the `divided_by` operator would return a rounded integer. It means calculations in Jekyll are more precise with this update. Anyways, to display the rounded number, there is a JavaScript snippet written by [Josh Bassett](https://twitter.com/nullobject). Just put it in the site's footer.

{% highlight javascript %}
{% raw %}
<script type='text/javascript'>
  $(document).ready(function() {
    $(".time").text(function (index, value) {
      return Math.round(parseFloat(value));
    });
  });
</script>
{% endraw %}
{% endhighlight %}

Now any floating point enclosed by the `<span class="time">12.3334455</span>` will be rounded by the JavaScript snippet.

Now that the JavaScript is in place, you can now display the calculated and rounded Estimated Reading time to the reader. Lets make things interesting. Lets make the ***User eXperience(UX)*** better by handling the pluralization of the word *"minute"* if its greater than 1. The basic idea is this, if the calculated reading time is less than 1 minute, display *"Less than 1 minute read"*, if its between 1 minute and 1 and a half minutes display *"1 minute read"*, and if its more than 1 and half minutes, display the *"calculated+rounded minutes read"*. Here is the code to achieve this:

{% highlight ruby %}
{% raw %}
{% if site.readtime %}
  {% if readtime < 1 %}Less than 1 minute read{% endif %}
  {% if readtime > 1 and readtime < 1.5 %}1 minute read{% endif %}
  {% if readtime > 1.5 %}<span class="time">{{ readtime }}</span> minutes read{% endif %}
{% endif %}
{% endraw %}
{% endhighlight %}

To display the Estimated Reading Time inside the Article page, the method is pretty straightforward. Simply put this code anywhere before using the `{% raw %}{{ readtime }}{% endraw %}` tag:

{% highlight ruby %}
{% raw %}
{% if site.readtime %}
  {% if site.wpm %}
    {% assign readtime = page.content | strip_html | number_of_words | append: '.0' | divided_by:site.wpm %}
  {% else %}
    {% assign readtime = page.content | strip_html | number_of_words | append: '.0' | divided_by:180 %}
  {% endif %}
{% endif %}
{% endraw %}
{% endhighlight %}

Then put the required markup as before to display the Estimated Reading Time(ERT) anywhere you like. You can wrap all these in your own styling, maybe add a [Font-Awesome Clock](http://fortawesome.github.io/Font-Awesome/icon/clock-o/) icon to it.

## **Requests?**

If you have some specific requests for this snippet, or if you need help custom coding, message me on Twitter @[hmfaysal](http://twitter.com/hmfaysal) or email me at [hmfaysal@alum.mit.edu](mailto:hmfaysal@alum.mit.edu)

If you'd like to give me credit somewhere on your blog or tweet a shout out to [@hmfaysal](https://twitter.com/hmfaysal), that would be pretty sweet.
