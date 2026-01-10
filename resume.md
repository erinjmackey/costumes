---
layout: default
title: Resume
permalink: /resume/
---

# Erin Mackey

## BFA Drama, BSc Computer Science, IATSE 212 Member

### Calgary, AB
<hr>
<section class="container my-5 resume-section" id="education">
  <h2 class="mb-4">Education</h2>
  
  {% for section in site.data.education %}
  <h3 class="h5 mt-4 text-uppercase text-muted">{{ section.category }}</h3>
  <table class="table table-hover">
    <tbody>
	{% assign courses = section.courses | sort:"date" | reverse %}
      {% for item in courses | sort:"date" | reverse %}
      <tr>
        <td class="col-4"><strong>{{ item.course }}</strong></td>
        <td class="col-3">{{ item.location }}</td>
		<td class="col-1">{{ item.date | date: "%Y" }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
  {% endfor %}
</section>
<hr>
<section class="container my-5 resume-section" id="awards">
  <h2 class="mb-4">Awards</h2> 
  <table class="table table-hover">
    <tbody>
	{% assign awards = site.data.awards | sort:"date" | reverse %}
      {% for item in awards %}
      <tr>
        <td class="col-4"><strong>{{ item.award }}</strong></td>
        <td class="col-3">{{ item.from }}</td>
		<td class="col-1">{{ item.date | date: "%Y" }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
</section>
<hr>
<section class="container my-5 resume-section" id="credits">
  <h2 class="mb-4">Credits</h2>
  
  {% for section in site.data.credits %}
  <h3 class="h5 mt-4 text-uppercase text-muted">{{ section.category }}</h3>
  <table class="table table-hover">
    <tbody>
	{% assign credits = section.credits | sort:"date" | reverse %}
      {% for item in credits | sort:"date" | reverse %}
      <tr>
        <td class="col-3"><strong>{{ item.title }}</strong></td>
        <td class="col-4">{{ item.show }}</td>
        <td class="col-3">{{ item.company }}</td>
		<td class="col-1">{{ item.date | date: "%Y" }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
  {% endfor %}
</section>
<hr>
<section class="container my-5 resume-section" id="skills">
  <h2 class="mb-4">Skills</h2>
  
  {% assign skillgroups = site.data.skills | group_by: "category" %}

	{% for skillgroup in skillgroups %}
	  <h3>{{ skillgroup.name }}</h3>
	  <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5">
		{% for skill in skillgroup.items %}
		{% assign percentage = skill.level | times: 100 | divided_by: 4 | round %}
      
		  <div class="col">
			  <span>
				  {{skill.skill}}
				  <div class="progress" role="progressbar">
					<div class="progress-bar" style="width: {{percentage}}%"></div>
				  </div>
			  </span>
		  </div>
		{% endfor %}
	  </div>
	{% endfor %}
</section>

{% include contact.html %}