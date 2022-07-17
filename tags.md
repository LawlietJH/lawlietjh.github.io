---
layout: page
permalink: /tags/
title: Tags
---

{% for tag in site.tags %}
  <div class="tags-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="#{{ tag_name | slugize }}"></div>
    <h2 class="tag-head">{{ tag_name }}</h2>
    <a name="{{ tag_name | slugize }}"></a>
    <ul>
    {% for post in site.tags[tag_name] %}
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