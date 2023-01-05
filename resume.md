---
title: Resume
layout: a4page
---

{% assign about_me = site.sections | where: "version", "short" | where: "section", "about" | first %}
{% assign experiences = site.experiences | where: "resume", true %}

<div id="cv">
    <div class="mainDetails">
        <div id="name">
            <h1>Thomas Hareau</h1>
            <h2>Senior software engineer</h2>
        </div>

        <div id="contactDetails" class="quickFade delayFour">
            <ul>
                <li><a href="mailto:thomas@hareau.eu">thomas@hareau.eu</a></li>
                <li><a href="https://thomas.hareau.eu">thomas.hareau.eu</a></li>
                <li><a href="https://github.com/ThHareau">github.com/ThHareau</a></li>
            </ul>
        </div>
        <div class="clear"></div>
    </div>

    <div id="mainArea">
        <section>
            <article>
                <div class="sectionTitle">
                    <h1>{{ about_me.title }}</h1>
                </div>

                <div class="sectionContent">
                    {{ about_me.content | markdownify }}
                </div>
            </article>
            <div class="clear"></div>
        </section>


        <section>
            <div class="sectionTitle">
                <h1>Work experience</h1>
            </div>

            <div class="sectionContent">
                {% for experience in experiences reversed %}
                    <article>
                        <h2>{{ experience.position }} at {{ experience.company }}</h2>
                        <p class="subDetails">{{ experience.location }} - {{ experience.period }}</p>
                        <p>{{ experience.content }}</p>
                    </article>
                {% endfor %}
            </div>
            <div class="clear"></div>
        </section>


        <section>
            <div class="sectionTitle">
                <h1>Key Skills</h1>
            </div>

            <div class="sectionContent">
                <ul class="keySkills">
                    <li>Software architecture</li>
                    <li>Web development</li>
                    <li>Communication</li>
                    <li>JavaScript</li>
                    <li>Ruby</li>
                    <li>PHP</li>
                </ul>
            </div>
            <div class="clear"></div>
        </section>
        <section>
            <div class="sectionTitle">
                <h1>Education</h1>
            </div>

            <div class="sectionContent">
                <article>
                    <h2>INSA Rennes (France)</h2>
                    <p class="subDetails">Engineering degree</p>
                    <p>Software development (OOP, data structure, design pattern, software
                        modeling). Theoretical computer science (graph theory, algorithm),
                        hardware, social sciences.</p>
                </article>

                <article>
                    <h2>Technical University of Dresden (Germany)</h2>
                    <p>Software technology (software architecture, component-based system
                        engineering, web protocols). Research (shared locked analysis,
                        synchronization of a satellite software within a DTN simulator).</p>
                </article>
            </div>
            <div class="clear"></div>
        </section>
    </div>
</div>
