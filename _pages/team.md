---
layout: page
permalink: /people/
title: People
description: #team
nav: true
nav_order: 2
---

<h2>Current</h2>
<div class="row g-3">
  {% for person in site.data.people.current_phd %}
    <div class="col-12 col-md-6">
      {% include person.liquid person=person %}
    </div>
  {% endfor %}
  {% for person in site.data.people.current_master %}
    <div class="col-12 col-md-6">
      {% include person.liquid person=person %}
    </div>
  {% endfor %}
</div>
<h2>Alumni</h2>
<div class="row g-3">
  {% for person in site.data.people.alumni %}
    <div class="col-12 col-md-6">
      {% include person.liquid person=person %}
    </div>
  {% endfor %}
</div>
