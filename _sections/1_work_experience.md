---
title: Work Experience
section: experience
rank: 2
version: long
---


{% for experience in site.experiences reversed %}
<div class="item">
    <h3 class="title">{{ experience.position }}
        <span class="place"> —
            {% if experience.link %}
                <a href="{{ experience.link }}">{{ experience.company }}</a>
            {% else %}
                {{ experience.company }}
            {% endif %}
        </span>
        <span class="year">({% if experience.location %}{{ experience.location }} - {% endif %}{{ experience.period }})</span>
    </h3>
    <p> {{ experience.content | markdownify }} </p>
</div>
{% endfor %}

<p><a class="more-link" href="https://www.linkedin.com/in/thomas-hareau-742b8085/#experience"><i class="fa fa-external-link"></i> More on LinkedIn</a></p>
