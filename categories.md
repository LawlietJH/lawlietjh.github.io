---
layout: page
permalink: /categories
title: Categories
description: Lista de Categorías.
page_id: 4
---

{% assign site_categories_sort = site.categories | sort %}
<p class="tabs-textcolor">Categorías:</p>
<ul class="tag-column-list-2">
  {% for category in site_categories_sort %}
    <li class="categories-link-mark">
      <a href="#{{category | first }}" class="categories-link-capsule">
        {{category | first }}
      </a>
    </li>
  {% endfor %}
</ul>
<div><br><hr><br></div>
{% for category in site_categories_sort %}
  <div class="category-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="{{ category_name | slugize }}"><br></div>
    <h2 class="category-head">
      <a href="#{{ category_name | slugize }}" class="categories-link-capsule categories-link-capsule-title">
        {{ category_name }}
      </a>
    </h2>
    <ul>
      {% assign site_time = site.time | date: '%s' | plus: 0 %}
      {% for post in site.categories[category_name] %}
        {% assign post_date = post.date | date: '%s' | plus: 0 %}
        {% if site_time >= post_date or site.debug == true %}
          <li>
            <h3>
                <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}" class="categories-link-capsule categories-link-capsule-content">
                  {{post.title}}
                </a><br>
                <time>{{ post.date | date:"%d %b %Y" }}</time>
            </h3>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
{% endfor %}
