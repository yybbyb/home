---
layout: page
permalink: /members/
title: Members
description: 에너지AI·계산과학실 구성원
nav: true
nav_order: 2
---

{% assign teams = "atomic,cfd,process,data-ai" | split: "," %}
{% assign team_names = "원자단위 전산모사,전산유체역학,공정/엔지니어링,AI·데이터 과학" | split: "," %}

{% for team in teams %}
{% assign idx = forloop.index0 %}

### {{ team_names[idx] }}

<table>
  <thead>
    <tr>
      <th>이름</th>
      <th>직급</th>
    </tr>
  </thead>
  <tbody>
{% assign team_members = site.data.members | where: "team", team %}
{% for member in team_members %}
    <tr>
      <td>
        {% if member.external_url and member.external_url != "" %}
        <a href="{{ member.external_url }}" target="_blank">{{ member.name }}</a>
        {% else %}
        <a href="{{ site.baseurl }}/members/{{ member.id }}/">{{ member.name }}</a>
        {% endif %}
      </td>
      <td>{{ member.position }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>

---

{% endfor %}
