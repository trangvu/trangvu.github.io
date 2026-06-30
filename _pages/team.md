---
layout: page
permalink: /people/
title: People
description: #team
nav: true
nav_order: 2
---
<style>
.roster { border-top: .5px solid var(--global-divider-color); margin-bottom: 2.5rem; }
.roster .row {
  display: flex; align-items: baseline; gap: .9rem;
  padding: .5rem 0; border-bottom: .5px solid var(--global-divider-color);
}
.roster .row:hover .name { color: var(--global-theme-color); }
.roster .info { flex: 1; min-width: 0; }
.roster .name { font-weight: 600; color: inherit; text-decoration: none; }
.roster .name:hover { color: var(--global-theme-color); }
.roster .topic { font-size: .82rem; color: var(--global-text-color-light); }
.roster .sub   { font-size: .82rem; color: var(--global-text-color-light); margin-top: .2rem; }
.roster .meta  { text-align: right; flex-shrink: 0; white-space: nowrap; }
.roster .year  { font-size: .82rem; color: var(--global-text-color-light); margin-top: .3rem; }
.badge { display:inline-block; font-size:.72rem; padding:2px 8px; border-radius:5px; }
.b-phd    { background:#1e3a8a; color:#1e3a8a; }
.b-master { background:#920e87; color:#074668; }
.b-main   { background:#166534; color:#166534; }
.b-co     { background:#92400e; color:#92400e; }
.roster-head {
  display:flex; align-items:baseline; justify-content:space-between;
  margin: 2rem 0 .35rem; font-size:.8rem; letter-spacing:.05em;
  text-transform:uppercase; color:var(--global-text-color-light);
}
.roster-head:first-of-type { margin-top: 1rem; }
@media (max-width: 576px) {
  .roster .row { flex-direction: column; gap: .25rem; }
  .roster .meta { text-align: left; }
}


</style>

<!-- <h3> Current </h3> -->
{% assign current = "PhD,Master" | split: "," %}
{% for grp in current %}
  {% if grp == "PhD" %}{% assign people = site.data.people.current_phd | sort: 'start' | reverse %}
{% else %}{% assign people = site.data.people.current_master | sort: 'start' | reverse %}{% endif %}
  <div class="roster-head"><span>Current {{ grp }}</span><span>{{ people | size }}</span></div>
  <div class="roster">
  {% for p in people %}
    <div class="row">
      <div class="info">
        <a class="name" href="{{ p.website | default: '#' }}"{% if p.website %} target="_blank" rel="noopener"{% endif %}>{{ p.name }}</a>{% if p.topic %}<span class="topic"> --- {{ p.topic }}</span>{% endif %}
        <div class="sub">{% if p.joint_with %}with {{ p.joint_with }} {% endif %}</div>
      </div>
      <div class="meta">
        <span class="badge {% if p.degree == 'PhD' %}b-phd{% else %}b-master{% endif %}">{{ p.degree }}</span>
        <span class="badge {% if p.role contains 'Main' %}b-main{% else %}b-co{% endif %}">{% if p.role contains 'Main' %}Main Supervisor{% else %}Co-Supervisor{% endif %}</span>
        <div class="year">{{ p.start }}--</div>
      </div>
    </div>
  {% endfor %}
  </div>
{% endfor %}

<!-- <h3> Alumni </h3> -->
<div class="roster-head"><span>Alumni</span><span>{{ site.data.people.alumni | size }}</span></div>
<div class="roster">
{% assign alumni = site.data.people.alumni | sort: 'end' | reverse %}
{% for p in alumni %}
  <div class="row">
      <div class="info">
        <a class="name" href="{{ p.website | default: '#' }}"{% if p.website %} target="_blank" rel="noopener"{% endif %}>{{ p.name }}</a> {% if p.placement %}<span class="topic"> ➡️ {{ p.placement }}</span>{% endif %}
        <!-- {% if p.joint_with %} <span class="topic">with {{ p.joint_with }} </span> {% endif %} -->
        {% if p.thesis %}<div class="sub"> <b>Thesis:</b> {{ p.thesis }}</div>{% endif %}
        <!-- <div class="sub">{% if p.placement %}-> {{ p.placement }} {% endif %}</div> -->
      </div>
      <div class="meta">
        <span class="badge {% if p.degree == 'PhD' %}b-phd{% else %}b-master{% endif %}">{{ p.degree }}</span>
        <span class="badge {% if p.role contains 'Main' %}b-main{% else %}b-co{% endif %}">{% if p.role contains 'Main' %}Main Supervisor{% else %}Co-Supervisor{% endif %}</span>
        <div class="year">{% if p.start and p.start != p.end %}{{ p.start }} -- {{ p.end }}{% else %}{{ p.end }}{% endif %}</div>
      </div>
    </div>
{% endfor %}
</div>