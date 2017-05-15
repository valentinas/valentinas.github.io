---
title: Home
---
### Recent Posts
{% for post in site.posts do %}
* {{ post.date }} [{{ post.title }}]({{ post.url }})
{% endfor %}

