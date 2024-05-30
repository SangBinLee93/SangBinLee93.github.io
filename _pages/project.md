---
title: "Project Archive (Demo Reel BreakDown)"
layout: single
permalink: /PROJECT/
entries_layout: grid
classes: wide
author_profile: false
---
- This page is still being edited(2024-05-30)

{% assign custom_order = "Personal,Animation,VFX,Script,Commercial,ETC" | split: ',' %}
{% assign ordered_collections = "" | split: '' %}

{% for collection_name in custom_order %}
  {% for collection in site.collections %}
    {% if collection.label == collection_name %}
      {% assign ordered_collections = ordered_collections | push: collection %}
    {% endif %}
  {% endfor %}
{% endfor %}

{% for collection in ordered_collections %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2 id="{{ label | slugify }}" class="archive__subtitle" align="center">{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
  {% endunless %}
  {% for post in collection.docs %}
    {% unless collection.output == false or collection.label == "posts" %}
    {% include archive-single.html type="grid"%}
    {% endunless %}
  {% endfor %}
  {% if label == "Animation" %}
  <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
  {% elsif label == "Commercial" %}
  <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
  {% else %}
  <br><br><br><br><br><br><br><br><br><br>
  {% endif %}
{% endfor %}
