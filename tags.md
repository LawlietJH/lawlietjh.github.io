---
layout: page
permalink: /tags
title: Tags
description: Lista de Tags.
page_id: 5
---

{% assign site_tags_sort = site.tags | sort %}
<p class="tabs-textcolor">Tags:</p>
<ul class="tag-column-list">
  {% for tag in site_tags_sort %}
    <li class="tags-link-mark">
      <a href="#{{tag | first }}" class="tags-link-capsule">
        {{tag | first }}
      </a>
    </li>
  {% endfor %}
</ul>
<div><br><hr><br></div>
{% for tag in site_tags_sort %}
  <div class="tags-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="{{ tag_name | slugize }}"><br></div>
    <h2 class="tag-head">
      <a href="#{{ tag_name | slugize }}" class="tags-link-capsule tags-link-capsule-title">
        {{ tag_name }}
      </a>
    </h2>
    <ul>
      {% assign site_time = site.time | date: '%s' | plus: 0 %}
      {% for post in site.tags[tag_name] %}
        {% assign post_date = post.date | date: '%s' | plus: 0 %}
        {% if site_time >= post_date or site.debug == true %}
          <li>
            <h3>
                <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}" class="tags-link-capsule tags-link-capsule-content">
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
