---
title: "Categories"
layout: single
permalink: /categories/
collection_ref: lessons
taxonomy_field: categories
taxonomy_grouping: true
sidebar:
  nav: "learn"
---

<div class="taxonomy-hero">
  <svg class="taxonomy-hero__curve" viewBox="0 0 800 100" preserveAspectRatio="none" aria-hidden="true">
    <defs>
      <linearGradient id="tax-grad" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="#38547a" stop-opacity="0"/>
        <stop offset="50%" stop-color="#8ab4cc" stop-opacity="0.5"/>
        <stop offset="100%" stop-color="#38547a" stop-opacity="0"/>
      </linearGradient>
    </defs>
    <path d="M0,60 C120,20 240,80 360,50 C480,20 600,80 720,40 C760,25 790,65 800,50"
          fill="none" stroke="url(#tax-grad)" stroke-width="1.5" stroke-linecap="round"/>
    <path d="M0,80 C180,50 300,70 420,55 C540,40 660,75 800,60"
          fill="none" stroke="url(#tax-grad)" stroke-width="1" stroke-linecap="round" opacity="0.4"/>
  </svg>
  <h2>Browse by Category</h2>
  <p>Categories group lessons into broad areas of study. Click one to jump to its section, or scroll through everything below.</p>
</div>

<div markdown="0">
{% include lessons-by-taxonomy.html %}
</div>
