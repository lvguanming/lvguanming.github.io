---
layout: page
permalink: /update-log/
title: "更新日志"
description: 
modified: 2014-09-03 13:52:42 +0600
tags: []
jquery: true
---
## 本站最近 30 条更新日志



<div id="github-commits"></div>


<script src="{{ site.url }}/assets/js/vendor/github.commits.widget.js"></script>

<script>
$(function() {
	$('#github-commits').githubInfoWidget(
		{ user: 'lvguanming', repo: 'lvguanming.github.io', branch: 'master', last: 30, limitMessageTo: 30 });
});
</script>  