---
layout: single
title: John McEwan's CV
permalink: /cv/
---

<div class="cv-container">

<h1>{{ site.data.cv.name }}</h1>

<div class="contact-info">
  <p>Email: <a href="mailto:{{ site.data.cv.contact.email }}">{{ site.data.cv.contact.email }}</a></p>
  <p>LinkedIn: <a href="{{ site.data.cv.contact.linkedin }}">{{ site.data.cv.contact.linkedin }}</a></p>
</div>

<h2>Top Skills</h2>
<ul>
{% for skill in site.data.cv.skills %}
  <li>{{ skill.description }}</li>
{% endfor %}
</ul>

<h2>Professional Registrations</h2>
<ul>
{% for certification in site.data.cv.certifications %}
  <li>{{ certification.title }} - {{ certification.body }}</li>
{% endfor %}
</ul>

<h2>Professional Summary</h2>
<p>{{ site.data.cv.summary }}</p>

<h2>Previous Experience</h2>
{% for item in site.data.cv.previous_experience %}
  <div class="previous-experience">
    <h3>{{ item.title }}</h3>
    <p>Company: {{ item.company }}, Location: {{ item.location }}</p>
    <p>Duration: {{ item.duration }}</p>
    <p>{{ item.description }}</p>
  </div>
{% endfor %}

<h2>Education</h2>
{% for education in site.data.cv.education %}
  <div class="education">
    <h3>{{ education.degree }}</h3>
    <p>Institution: {{ education.institution }}, Dates: {{ education.dates }}</p>
  </div>
{% endfor %}



</div>
