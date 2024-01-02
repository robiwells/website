---
layout: archive
permalink: /education/
---

{% include base_path %}
{% for post in site.posts %}
    {% if post.categories contains 'education' %}
        {% include archive-single.html %}
    {% endif %}
{% endfor %}