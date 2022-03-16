---
layout: page
permalink: /publications/
title: publications
years: [2021,2020]
nav: true
---
<!-- _pages/publications.md -->
<div class="publications">

<h2 class="year">in press</h2>
{% bibliography -f inpress %}

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
