---
layout: page
permalink: /teaching/
title: Teaching
description: #classes, workshops, and teaching material
nav: true
nav_order: 3
---
<style>
.courses { border-top: .5px solid var(--global-divider-color); }
.courses details { border-bottom: .5px solid var(--global-divider-color); }
.courses summary {
  display: flex; align-items: baseline; gap: .75rem;
  padding: .7rem 0; cursor: pointer; list-style: none;
}
.courses summary::-webkit-details-marker { display: none; }
.courses .chev { font-size: 1rem; color: var(--global-text-color-light); transition: transform .15s; flex-shrink: 0; }
.courses details[open] .chev { transform: rotate(90deg); }
.courses .info { flex: 1; min-width: 0; }
.courses .title { font-weight: 600; }
.courses .code  { font-size: .82rem; color: var(--global-text-color-light); }
.courses .blurb { font-size: .82rem; color: var(--global-text-color); margin-top: .15rem; }
.courses .meta  { text-align: right; flex-shrink: 0; white-space: nowrap; }
.courses .year  { font-size: .82rem; color: var(--global-text-color-light); margin-top: .3rem; }
.courses .syllabus { padding: .25rem 0 1rem 1.75rem; font-size: .9rem; color: var(--global-text-color); line-height: 1.7; }
.courses .syllabus ul { margin: .4rem 0 0; padding-left: 1.1rem; }
.badge { display:inline-block; font-size:.72rem; padding:2px 8px; border-radius:5px; }
.b-lect { background:#2f8d6c; color:#993C1D; }
.b-ta   { background:#9f4221; color:#085041; }
.courses-head {
  font-size:.8rem; letter-spacing:.05em; text-transform:uppercase;
  color:var(--global-text-color-light); margin-bottom:.25rem;
}
@media (max-width: 576px) {
  .courses summary { flex-wrap: wrap; }
  .courses .meta { text-align: left; }
}
</style>

<div class="courses-head">Monash University</div>
<div class="courses">
{% for c in site.data.teaching %}
  <details{% if c.open %} open{% endif %}>
    <summary>
      <i class="ti ti-chevron-right chev"></i>
      <div class="info">
        <span class="title">{{ c.title }}</span><span class="code"> · {{ c.code }}</span>
        {% if c.blurb %}<div class="blurb">{{ c.blurb }}</div>{% endif %}
      </div>
      <div class="meta">
        <span class="badge {% if c.role == 'TA' %}b-ta{% else %}b-lect{% endif %}">{{ c.role | default: 'Lecturer' }}</span>
        <div class="year">{{ c.year }}</div>
      </div>
    </summary>
    <div class="syllabus">{{ c.syllabus | markdownify }}</div>
  </details>
{% endfor %}
</div>