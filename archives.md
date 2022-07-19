---
layout: page
permalink: /archives
title: Archives
---

<section>
  {% if site.posts[0] %}

    {% capture currentyear %}
      {{ 'now' | date: "%Y" }}
    {% endcapture %}
    {% capture firstpostyear %}
      {{ site.posts[0].date | date: '%Y' }}
    {% endcapture %}
    {% if currentyear == firstpostyear %}
        <div id="Recientes"></div>
        <h3 class="archives-head">
          <a href="#Recientes">
            Recientes
          </a>
        </h3>
    {% else %}
        <div id="{{ firstpostyear }}"></div>
        <h3 class="archives-head">
          <a href="#{{ firstpostyear }}">
            {{ firstpostyear }}
          </a>
        </h3>
    {% endif %}

    {% assign site_time = site.time | date: '%s' | plus: 0 %}
    {%for post in site.posts %}
      {% unless post.next %}
        <ul>
      {% else %}
        {% capture year %}
          {{ post.date | date: '%Y' }}
        {% endcapture %}
        {% capture nyear %}
          {{ post.next.date | date: '%Y' }}
        {% endcapture %}
        {% if year != nyear %}
          </ul>
          <div id="{{ post.date | date: '%Y' }}"></div>
          <h3 class="archives-head">
            <a href="#{{ post.date | date: '%Y' }}">
              {{ post.date | date: '%Y' }}
            </a>
          </h3>
          <ul>
        {% endif %}
      {% endunless %}
      {% assign post_date = post.date | date: '%s' | plus: 0 %}
      {% if site_time >= post_date or site.debug == true %}
        <li><time>{{ post.date | date:"%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ post.title }}
          </a>
        </li>
      {% endif %}
    {% endfor %}
    </ul>

  {% endif %}
</section>
