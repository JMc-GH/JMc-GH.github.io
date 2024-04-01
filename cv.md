---
layout: page
title: CV
permalink: /cv/
---

<div class="cv-container">

<h2><u><strong>John McEwan</strong></u></h2>

<h2>Professional Summary</h2>
<p>{{ site.data.cv.summary }}</p>

<h2>Professional Memberships</h2>
<ul>
{% for certification in site.data.cv.certifications %}
  <li>{{ certification.title }} - {{ certification.body }}</li>
{% endfor %}
</ul>

<h2>Professional Experience</h2>
{% for experience in site.data.cv.experience %}
  <div class="experience">
    <h3>{{ experience.title }}</h3>
    <p>Company: {{ experience.company }}, Location: {{ experience.location }}</p>
    <p>Duration: {{ experience.duration }}</p>
    <p>{{ experience.description }}</p>
  </div>
{% endfor %}

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

<div class="contact-info">
  <p>Email: <a href="mailto:{{ site.data.cv.contact.email }}">{{ site.data.cv.contact.email }}</a></p>
  <p>LinkedIn: <a href="{{ site.data.cv.contact.linkedin }}">{{ site.data.cv.contact.linkedin }}</a></p>
</div>



</div>