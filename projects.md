---
layout: page
permalink: /projects/
title: Projects
class: projects
---

{:.hidden}
# Projects

{:.lead}
Research tools, open-source contributions, and side projects. Code on [GitHub](https://github.com/Aniketh01).

<div class="project-list">
  {% for project in site.data.projects %}
    {% include project.html project=project %}
  {% endfor %}
</div>
