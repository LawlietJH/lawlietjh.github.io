---
layout: page
permalink: /archives
title: Archives
description: Lista de todas las publicaciones del Blog.
page_id: 3
---

<section>
  {% if site.posts[0] %}
    {% capture current_month %}
      {{ 'now' | date: "%Y %B" }}
    {% endcapture %}
    {% capture first_post_month %}
      {{ site.posts[0].date | date: '%Y %B' }}
    {% endcapture %}
    {% if current_month == first_post_month %}
        <div id="Recientes"></div>
        <h3 class="archives-head">
          <a href="#Recientes">
            Recientes
          </a>
        </h3>
    {% else %}
        <div id="{{ site.posts[0].date | date: '%Y-%B' }}"></div>
        <h3 class="archives-head">
          <a href="#{{ site.posts[0].date | date: '%Y-%B' }}">
            {{ first_post_month }}
          </a>
        </h3>
    {% endif %}
    {% assign site_time = site.time | date: '%s' | plus: 0 %}
    {%for post in site.posts %}
      {% unless post.next %}
        <ul>
      {% else %}
        {% capture year %}
          {{ post.date | date: '%Y %B' }}
        {% endcapture %}
        {% capture nyear %}
          {{ post.next.date | date: '%Y %B' }}
        {% endcapture %}
        {% if year != nyear %}
          </ul>
          <div id="{{ post.date | date: '%Y-%B' }}"></div>
          <h3 class="archives-head">
            <a href="#{{ post.date | date: '%Y-%B' }}">
              {{ post.date | date: '%Y %B' }}
            </a>
          </h3>
          <ul>
        {% endif %}
      {% endunless %}
      {% assign post_date = post.date | date: '%s' | plus: 0 %}
      {% if site_time >= post_date or site.debug == true %}
        <li class="archives-link-mark">
          <time>{{ post.date | date:"%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}" class="archives-link-capsule">
            {{ post.title }}
          </a>
        </li>
      {% endif %}
    {% endfor %}
    </ul>
  {% endif %}
</section>
