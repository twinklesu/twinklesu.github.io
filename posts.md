---
layout: page
permalink: /posts/
title: POST
description: Showcase your writing, short stories, or poems. Replace this text with your description.
---

<ul class="post-list">
{% for post in site.posts%}
    <li>
        <h3><a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h3>
        <p class="post-meta">{{ post.date | date: '%B %-d, %Y — %H:%M' }}</p>
      </li>
{% endfor %}
</ul>