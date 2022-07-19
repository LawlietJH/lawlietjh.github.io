---
layout: page
permalink: /tags
title: Tags
---

{% assign site_tags_sort = site.tags | sort %}
{% for tag in site_tags_sort %}
  <div class="tags-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="{{ tag_name | slugize }}"><br></div>
    <h2 class="tag-head">
      <a href="#{{ tag_name | slugize }}">
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
              <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">{{post.title}}</a><br>
              <time>{{ post.date | date:"%d %b %Y" }}</time>
          </h3>
        </li>
      {% endif %}
    {% endfor %}
    </ul>
  </div>
{% endfor %}
