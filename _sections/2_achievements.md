---
title: Achievements
section: projects
rank: 3
version: long
---

{% for achievement in site.achievements %}
<div class="item">
    <h3 class="title">{{ achievement.title }} ({{ achievement.period }})</h3>
    <div class="row">
        <div class="col-sm-10">
            <p class="summary">
                {{ achievement.content }}
            </p>
            <p>
                <a class="more-link"
                   href="{{ achievement.link }}"><i
                        class="fa {{ achievement.icon }}"></i> Find out more</a>
            </p>
        </div>
        <div class="col-sm-2 text-center">
            <table class="table table-condensed">
                {% for language in achievement.languages %}
                     <tr><td>{{ language }}</td></tr>
                {% endfor %}
            </table>
        </div>
    </div>
</div>    
{% endfor %}
