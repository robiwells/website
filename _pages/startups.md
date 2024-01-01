---
layout: archive
permalink: /startups/
---

{% include base_path %}
{% for post in site.posts %}
    {% if post.categories contains 'startups' %}
        {% include archive-single.html %}
    {% endif %}
{% endfor %}