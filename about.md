---
layout: page
permalink: /about/
title: 关于
tags: [吕管明]
imagefeature: fourseasons.jpg
chart: true
charttype: pie
---
<figure>
  <img src="{{ site.imageurl }}/me-and-myself.jpg" alt="我和自己">
  <figcaption>吕管明</figcaption>
</figure>

{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign total_words = total_words | plus: post_words %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}
{% for status in site.data.statuses %}{% assign statuscount = statuscount | plus:1 %}{% endfor %}

欢迎来访 **《吕管明的网络日志》**, 这是我的个人网站。到目前为止，一共写了{{ site.posts | size }}篇文章，分别发布在{{ site.categories | size }}个分类下。{% if featuredcount != 0 %}其中，共有<a href="{{ site.url }}/featured">{{ site.categories | size }}篇</a>精选文章，推荐给你。{% endif %}最近写的{% for post in site.posts limit:1 %}{% if post.description %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="阅读 {{ post.title }}">"{{ post.title }}"</a>{% endif %}{% endfor %}于{% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%Y年%m月%d日%H点%M分" }}</time>发布。{% if post.modified %}{% if modifiedtime != posttime %} 并且于<time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%Y年%m月%d日%H点%M分" }}</time>做了更新。{% endif %}{% endif %}{% endfor %}最后一次提交于 {{ site.time | date: "%Y年%m月%d日%H点%M分" }}。查看所有更新日志，可以点击 [这里]({{ site.url }}/update-log)。

共发布了 [{{ statuscount }} 条状态信息]({{ site.url }}/status-updates-archive)。

<div class="chart" id="chartdiv" style="width: 100%; height: 500px; margin-bottom: 20px;" ></div>

##关于我##

中国内蒙人，80后，集“农民、工人、知识分子等多种身份”于一身，非国家“985”、“211”院校计算机专业本科毕业，爱好技术和文学；专注于科技和人文方面的知识和技能，我对一切未知的东西保持敬畏，具备起码的审美能力，从小就有几个梦想——发明家、作家、科学家。:-)
大学时在东北，现为北漂「IT工程师」。没什么吹的，这里省略X个字。

<figure>
	<img src="{{ site.imageurl }}/20100818336.jpg" alt="2010">
	<figcaption>2010年，长春农业博览会</figcaption>
</figure>

我出生在内蒙古呼和浩特南部一个比较偏远的山区，没错，是内蒙古，是个有牛羊却没有草原的地方，一望无际的是沟壑纵横、支离破碎的黄土高原地貌；虽属内蒙古，但有的却是典型的陕北风土人情。由于要上学，不得不离开长大的地方，走进城市，开始时都无法适应陌生的城市，事实证明，时间久了，总是会喜欢上常年呆过的城市，正所谓日久生情。而每个城市有每个城市的性格，也影响着人的性格。我所呆过的城市，将我彻底改变，随着时代的变迁和时间的推移，所有的改变，导致的结果是再也回曾不去长大的农村，同时也很难成为一个名副其实的城市人。即使如此，我还是非常喜欢我所呆过的三座城市。

<figure class="third">
	<a href="{{ site.url }}/images/about/1.jpg" title="家乡"><img src="{{ site.url }}/images/about/1-001.jpg"></a>
	<a href="{{ site.url }}/images/about/2.jpg" title="牛羊下来"><img src="{{ site.url }}/images/about/2-001.jpg"></a>
	<a href="{{ site.url }}/images/about/3.jpg" title="放羊的人"><img src="{{ site.url }}/images/about/3-001.jpg"></a>
</figure>
<figure class="half">
	<a href="{{ site.url }}/images/about/4.jpg" title="长春工程学院"><img src="{{ site.url }}/images/about/4-001.jpg"></a>
	<a href="{{ site.url }}/images/about/5.jpg" title="假期里安静的校园"><img src="{{ site.url }}/images/about/5-001.jpg"></a>
</figure>
<figure class="third">
	<a href="{{ site.url }}/images/about/6.jpg" title="颐和园南路"><img src="{{ site.url }}/images/about/6-001.jpg"></a>
	<a href="{{ site.url }}/images/about/7.jpg" title="夜行长安街"><img src="{{ site.url }}/images/about/7-001.jpg"></a>
	<a href="{{ site.url }}/images/about/8.jpg" title="被盗的爱车"><img src="{{ site.url }}/images/about/8-001.jpg"></a>
	<figcaption>这是一些非常有趣的记录</figcaption>
</figure>

我只去过国内一些城市，但目前还没出过国。呼和浩特、长春、北京——我呆过的三个城市，都给我我太多太多。

<figure>
	<img src="{{ site.imageurl }}/my-city.jpg" alt="重要的地方">
	<figcaption>三个对我重要影响深远的城市(截至2014年)</figcaption>
</figure>

##关于网站##
2012年5月，工信部消息称开放`.CN`域名个人注册，这真是个好消息，就在儿童节的那天，注册了现在这个域名：`lvgm.cn`，喜欢的是——“lvgm”正好是当时工作单位的员工ID，“cn”是中国的意思(我是中国人)。从此，在国际互联网上有了自己的唯一标识，因此兴奋了好久。也是从这时起对域名这种虚拟的东西产生了兴趣。

之前的个人网站建立在网站空间和AWS上，主要是为了玩。基本没写什么东西，也没有让人知道。直到GitHub的出现，2014年春运期间，GitHub因服务器被表面上毫不相干的中国春运抢票潮给拖垮而闻名中国IT界，从此红遍了中国。GitHub的伟大之处在于人们可以在上面自由创造、分享和发掘好东西，是之所以号称程序员的Facebook的原因。GitHub提供的GitHub Pages的另类绝佳的博客解决方案，绑定域名后就是个人网站了，决定把网站转移到GitHub，从此不再浪迹天涯了。希望今后能在其上面创造奇妙的东西。

在这里，预计可能会有：学习笔记，工作备忘，生活记录，扯淡杂谈。

```
做我爱做的事，爱我所做的事。
I make what I love，I love what I do.
```

总之：

- 作为一个IT互联网技术从业者，很应该需要有这么个东西。
- 作为一个热爱生活的人，有必要分享一些有用的东西为这个世界。
- 信息爆炸的时代，需要找个地方安顿一下浮躁、混乱不堪心。
- 找回人类应该有的思考能力，试图找到文字的力量。
- 可以满足若干种兴趣爱好。

嗯，这里可以创造一切的可能。

<!-- amCharts javascript code -->
<script type="text/javascript">
	AmCharts.makeChart("chartdiv",
		{
			"type": "pie",
			"pathToImages": "http://cdn.amcharts.com/lib/3/images/",
			"balloonText": "分类: [[title]]<br><span style='font-size:14px'><b>[[value]] 篇文章</b> ([[percents]]%)</span>",
			"innerRadius": "40%",
			"minRadius": 100,
			"pullOutRadius": "15%",
			"startRadius": "30%",
			"colors": [
				"#FC913A",
				"#F9D423",
				"#FF4E50",
				"#FCD202",
				"#F8FF01",
				"#B0DE09",
				"#04D215",
				"#0D8ECF",
				"#0D52D1",
				"#2A0CD0",
				"#8A0CCF",
				"#CD0D74",
				"#754DEB",
				"#DDDDDD",
				"#999999",
				"#333333",
				"#000000",
				"#57032A",
				"#CA9726",
				"#990000",
				"#4B0C25"
			],
			"hoverAlpha": 0.74,
			"pullOutEffect": "elastic",
			"pullOutOnlyOne": true,
			"startEffect": "easeOutSine",
			"titleField": "category",
			"valueField": "number-of-posts",
			"allLabels": [],
			"balloon": {},
			"legend": {
				"align": "center",
				"markerType": "diamond",
				"switchable": false,
				"textClickEnabled": true,
				"useMarkerColorForLabels": true,
				"useMarkerColorForValues": true,
				"valueText": "[[value]] 篇文章"
			},
			"titles": [
				{
					"id": "Title-1",
					"text": "分类文章数"
				}
			],
      "dataProvider": [
{% assign tags_list = site.categories %}  
  {% if tags_list.first[0] == null %}
    {% for tag in tags_list %} 
        {
          "category": "{{ tag | capitalize }}",
          "number-of-posts": {{ site.tags[tag].size }}
        },
    {% endfor %}
  {% else %}
    {% for tag in tags_list %} 
        {
          "category": "{{ tag[0] | capitalize }}",
          "number-of-posts": {{ tag[1].size }}
        },
    {% endfor %}
  {% endif %}
{% assign tags_list = nil %}
      ]
    }
  );
</script>
