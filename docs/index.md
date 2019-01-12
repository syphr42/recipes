---
title: Recipes
---

*This site contains a collection of recipes that I find interesting. Attribution is recorded where it is known.*

# Recent Additions

<ul>
  {% for post in site.posts limit:5 %}
    <li>
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a> <small>&lt;{{ post.date | date_to_string }}&gt;</small></a>
    </li>
  {% endfor %}
</ul>

# Categories

{% comment %}
=======================
The following part extracts all the categories from your posts and sort them, so that you do not need to manually collect your categories to a place.
=======================
{% endcomment %}
{% assign rawcategories = "" %}
{% for post in site.posts %}
	{% assign rawcategories = rawcategories | append:post.category %}
{% endfor %}
{% assign rawcategories = rawcategories | split:'|' | sort %}

{% comment %}
=======================
The following part removes duplicated categories and invalid categories like blank.
=======================
{% endcomment %}
{% assign categories = "" %}
{% for category in rawcategories %}
	{% if category != "" %}
		{% if categories == "" %}
			{% assign categories = category | split:'|' %}
		{% endif %}
		{% unless categories contains category %}
			{% assign categories = categories | join:'|' | append:'|' | append:category | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}

{% for category in categories %}
## {{ category }}
<ul>
  {% for post in site.posts %}
    {% if post.category == category %}
    <li>
      <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }} <small>&lt;{{ post.date | date_to_string }}&gt;</small></a>
    </li>
    {% endif %}
  {% endfor %}
</ul>
{% endfor %}

# Tags

{% comment %}
=======================
The following part extracts all the tags from your posts and sort tags, so that you do not need to manually collect your tags to a place.
=======================
{% endcomment %}
{% assign rawtags = "" %}
{% for post in site.posts %}
	{% assign ttags = post.tags | join:'|' | append:'|' %}
	{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}

{% comment %}
=======================
The following part removes duplicated tags and invalid tags like blank tag.
=======================
{% endcomment %}
{% assign tags = "" %}
{% for tag in rawtags %}
	{% if tag != "" %}
		{% if tags == "" %}
			{% assign tags = tag | split:'|' %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}

{% for tag in tags %}
<a href="#{{ tag | slugify }}">{{ tag }}</a>
{% endfor %}