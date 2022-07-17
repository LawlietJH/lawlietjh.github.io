---
layout: page
permalink: /categories
title: Categories
category: Categories
---

{% for category in site.categories %}
  <!-- {% if category == null %}
    General
  {% endif %} -->
  <div class="category-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <h2 class="category-head">{{ category_name }}</h2>
    <a name="{{ category_name | slugize }}"></a>
    <ul>
    {% for post in site.categories[category_name] %}
    <li>
      <h3>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">{{post.title}}</a><br>
          <time>{{ post.date | date:"%d %b %Y" }}</time>
      </h3>
    </li>
    {% endfor %}
    </ul>
  </div>
{% endfor %}