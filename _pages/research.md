---
layout: archive
title: "Research"  
permalink: /research/
author_profile: true
---

{% assign paper_title_open = '<span style="color:#4682B4; font-weight:bold !important;">' %}
{% assign paper_title_close = '</span>' %}

## Job Market Paper

{% include paper_entry.html
   title="Market Power, Expectations, and Asset Prices"
   coauthors="Dalton Rongxuan Zhang"
   links="kr_jmp" %}

## Refereed Publications

<!-- The links are in links.yaml under the _data folder -->
<!-- The code for the paper_entry function are in paper_entry.html in the _includes folder -->

{% include paper_entry.html
   title="From Immediate Acceptance to Deferred Acceptance: Effects on School Admissions and Achievement in England"
   coauthors="Camille Terrier and Parag Pathak"
   status="Forthcoming at American Economic Journal: Applied Economics"
   links="fpf_ban" %}

## Working Papers

{% include paper_entry.html
   title="Price Markups or Wage Markdowns?"
   coauthors="Dalton Rongxuan Zhang"
   links="markup_markdown" %}

{% include paper_entry.html
   title="Asset Pricing with Capital-Skill Complementarities"
   links="second_year" %}

## Work in Progress

{% include paper_entry.html
   title="HANK with Joint Market Power"
   coauthors="Michael Cai and Dalton Rongxuan Zhang"
   %}

{% include paper_entry.html
   title="The Welfare Cost of Price Markups and Wage Markdowns"
   coauthors="Dalton Rongxuan Zhang"
   %}

{% include paper_entry.html
   title="Indebted Innovation"
   coauthors="Aditya Soenarjo"
   %}

<!-- {{ paper_title_open }} Joint Market Power and Macro-Finance Trends {{ paper_title_close }} <br>
with Dalton Rongxuan Zhang

{{ paper_title_open }} Monetary Policy Transmission in the Presence of Joint Market Power {{ paper_title_close }} <br>
with Dalton Rongxuan Zhang -->

<!-- {% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %} -->
