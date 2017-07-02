---
title: Recipes
---

This site contains a collection of recipes that I find myself making repeatedly. Attribution is recorded where it is known.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
