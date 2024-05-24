---
title: "Project Archive (Demo Reel BreakDown)"
layout: single
permalink: /PROJECT/
entries_layout: grid
classes: wide
author_profile: false
---

{% assign custom_order = "Personal,Animation,VFX,Script" | split: ',' %}
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
  <br><br><br><br><br><br><br><br><br><br><br><br><br><br>
{% endfor %}