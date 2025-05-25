---
layout: default
---

# ⛵ Sailing Log

Welcome to my sailing logbook. Below is a list of recorded outings and passages.

<table>
  <thead>
    <tr>
      <th>Date</th>
      <th>Title</th>
      <th>Location</th>
      <th>Conditions</th>
      <th>Crew</th>
    </tr>
  </thead>
  <tbody>
    {% for post in site.posts %}
    <tr>
      <td>{{ post.date | date: "%Y-%m-%d" }}</td>
      <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      <td>{{ post.location | default: "-" }}</td>
      <td>{{ post.conditions | default: "-" }}</td>
      <td>
        {% if post.crew %}
          {{ post.crew | join: ", " }}
        {% else %}
          -
        {% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>
