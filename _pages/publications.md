---
layout: page
permalink: /publications/
title: Publications
description: An up-to-date list is available on my <a href='https://scholar.google.com/citations?user=SDRPjegAAAAJ'>Google Scholar</a>.

sections:
  - bibquery: "@article"
    text: "Journal Articles"
  - bibquery: "@incollection"
    text: "Book Chapters"

years: [2024, 2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015]

nav: true
nav_order: 2
---

<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <p class="bibtitle">{{section.text}}</p>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>
