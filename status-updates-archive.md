---
layout: page
permalink: /status-updates-archive/
title: "状态更新归档"
description:
modified: 2014-09-03 14:00:24 +0800
---
<ul class="post-list">
{% for status in site.data.statuses %}
<li>
<a class="weibo-icon" href="http://service.weibo.com/share/share.php?appkey=2109953222&title=&quot;{{ status.message }}&quot;%20via%20&#64;学无才" title="分享到微博"><i class="fa fa-weibo faa-ring animated"></i> </a>{{ status.message }}<span class="entry-date"><time datetime="{{ status.date }}" itemprop="datePublished">{{ status.date | date: "%b %d, %Y" }}</time>
</li>
{% endfor %}
</ul>