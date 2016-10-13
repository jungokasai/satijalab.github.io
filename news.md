---
layout: default
title: News
permalink: /news/
---

<div class = "news-list">
	{% for date in site.data.news %}
		{% if date.location == "both" or date.location == "news" %}
			<h4>
				{{ date.date }}
			</h4>
			<p>
				{{ date.entry}}
			</p>
		{% endif %}
	{% endfor %}
</div>
