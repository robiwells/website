---
layout: archive
permalink: /coding/
---

{% include base_path %}
{% for post in site.posts %}
    {% if post.categories contains 'coding' %}
        {% include archive-single.html %}
    {% endif %}
{% endfor %}