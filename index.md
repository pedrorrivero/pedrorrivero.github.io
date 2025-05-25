---
layout: default
---

# ⛵ Sailing Log

Welcome to my sailing logbook. Below is a list of recorded outings and passages.

{% assign total_days = 0 %}
{% for post in site.posts %}
  {% if post.start and post.finish %}
    {% assign start = post.start | date: "%s" %}
    {% assign finish = post.finish | date: "%s" %}
    {% assign seconds = finish | minus: start %}
    {% assign days = seconds | divided_by: 86400 %}
    {% assign days = days | plus: 1 %}
    {% assign total_days = total_days | plus: days %}
  {% endif %}
{% endfor %}

<p><strong>🗓️ Total Days at Sea:</strong> {{ total_days }}</p>

{% assign total_miles = 0 %}
{% for post in site.posts %}
  {% if post.miles %}
    {% assign total_miles = total_miles | plus: post.miles %}
  {% endif %}
{% endfor %}

<p><strong>⛵ Total Miles Sailed:</strong> {{ total_miles }}</p>

<table>
  <thead>
    <tr>
      <th>Date</th>
      <th>Title</th>
      <th>Location</th>
      <th>Nautical Miles</th>
      <th>Crew</th>
    </tr>
  </thead>
  <tbody>
    {% for post in site.posts %}
    <tr>
      <td>{{ post.date | date: "%Y-%m-%d" }}</td>
      <td><a href="{{ post.url }}">{{ post.title }}</a></td>
      <td>{{ post.location | default: "-" }}</td>
      <td>{{ post.miles | default: "-" }}</td>
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
