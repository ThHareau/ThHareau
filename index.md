---
title: Thomas Hareau
layout: default
sitemap: true
---

<div class="container">
    <div class="sections-wrapper">
        <div class="row">
            <div class="primary col-md-8 col-sm-12 col-xs-12">
                {% for section in site.sections %}
                <section class="{{ section.section }} section">
                    <div class="section-inner">
                        <h2 class="heading">{{ section.title }}</h2>
                        <div class="content">{{ section.content | markdownify }}</div>
                    </div>
                </section>
                {% endfor %}
            </div><!--//primary-->
            <div class="secondary col-md-4 col-sm-12 col-xs-12">

                {% include skills-aside.html %}
                {% include education-aside.html %}
                {% include languages-aside.html %}
            </div><!--//secondary-->
        </div><!--//row-->
    </div>
</div><!--//masonry-->
