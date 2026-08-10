---
layout: default
title: Blog Index
excerpt: Ideas, thoughts, and stories.
permalink: /posts/
image: '/assets/images/tech-abdul-jabbar-uses.webp'
lastmod: May 31 2026 08:55
---
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>