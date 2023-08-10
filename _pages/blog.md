---
layout: archive
permalink: /blog/
---

{% include base_path %}
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}