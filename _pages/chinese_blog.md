---
layout: default 
permalink: /chinese-blog/
title: 中文博客 
nav: true
nav_order: 4
pagination:
  enabled: true
  collection: chinese_posts
  permalink: /chinese-blog/page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---


<div class="post">

  <div class="header-bar">
    <h1>中文博客</h1>
    <h2>文章主要来自本科课程论文。本人学识有限，不免挂一漏万，君子谅焉。</h2>
  </div>

<div class="tag-category-list" style="text-align: center; margin-bottom: 20px;">
    <ul class="p-0 m-0">
      {% for tag in site.tags %}
        {% assign count = 0 %}
        {% for post in tag[1] %}{% if post.collection == 'chinese_posts' %}{% assign count = count | plus: 1 %}{% endif %}{% endfor %}
        {% if count > 0 %}
          <li style="display: inline-block; margin: 0 5px;">
            <i class="fa-solid fa-hashtag fa-sm"></i> 
            <a href="{{ tag[0] | slugify | prepend: '/chinese-blog/tags/' | relative_url }}">{{ tag[0] }}</a>
          </li>
        {% endif %}
      {% endfor %}
    </ul>

    <ul class="p-0 m-0" style="margin-top: 10px;">
      {% for category in site.categories %}
        {% assign count = 0 %}
        {% for post in category[1] %}{% if post.collection == 'chinese_posts' %}{% assign count = count | plus: 1 %}{% endif %}{% endfor %}
        {% if count > 0 %}
          <li style="display: inline-block; margin: 0 5px;">
            <i class="fa-solid fa-folder fa-sm"></i> 
            <a href="{{ category[0] | slugify | prepend: '/chinese-blog/categories/' | relative_url }}">{{ category[0] }}</a>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>

  <ul class="post-list">

    {% if page.pagination.enabled %}
      {% assign postlist = paginator.posts %}
    {% else %}
      {% assign postlist = site.chinese_posts | sort: 'date' | reverse %}
    {% endif %}

    {% for post in postlist %}

    {% assign read_time = post.content | strip_html | size | divided_by: 300 | plus: 1 %}
    {% assign year = post.date | date: "%Y" %}
    {% assign tags = post.tags | join: "" %}
    {% assign categories = post.categories | join: "" %}

    <li>
      {% if post.thumbnail %}
      <div class="row">
        <div class="col-sm-9">
      {% endif %}

        <h3>
          <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h3>
        
        <p>{{ post.description }}</p>

        <p class="post-meta">
          {{ read_time }} 分钟阅读 &nbsp; &middot; &nbsp;
          {{ post.date | date: '%Y-%m-%d' }}
        </p>

        <p class="post-tags">
          <a href="{{ year | prepend: '/chinese-blog/' | relative_url }}">
            <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}
          </a>

          {% if tags != "" %}
          &nbsp; &middot; &nbsp;
            {% for tag in post.tags %}
            <a href="{{ tag | slugify | prepend: '/chinese-blog/tags/' | relative_url }}">
              <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}
            </a>
            {% unless forloop.last %} &nbsp; {% endunless %}
            {% endfor %}
          {% endif %}
        </p>

      {% if post.thumbnail %}
        </div>
        <div class="col-sm-3">
          <img class="card-img" src="{{ post.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="image">
        </div>
      </div>
      {% endif %}

    </li>
    {% endfor %}
  </ul>

  {% if page.pagination.enabled %}
    {% include pagination.liquid %}
  {% endif %}

</div>