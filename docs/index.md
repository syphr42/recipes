---
title: Recipes
---

*This site contains a collection of recipes that I find interesting. Attribution is recorded where it is known.*

# Recent Additions

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
