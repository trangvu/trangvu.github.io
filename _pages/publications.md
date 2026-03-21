---
layout: page
permalink: /publications/
title: Publications
description: Publications by year in reversed chronological order.
years: [2026, 2025, 2024, 2023, 2022, 2021, 2020, 2019, 2018]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

  <h2>Preprints</h2>
  <details>
   <summary>Click to expand</summary>

  {% bibliography -f preprints --group_by year --group_order descending %}

  </details>
 <br> 
<h2 class="year">Peered-review</h2>
{%- for y in page.years %}
  
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
