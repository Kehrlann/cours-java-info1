---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: Liste des cours
---

{% for post in site.posts reversed %}

<li>
    <span>{{ post.date | date: "%d / %m / %Y" }} :&nbsp;</span>
    <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
</li>
{% endfor %}
