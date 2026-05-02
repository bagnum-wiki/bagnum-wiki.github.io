---
title: Current Roster
---

<h1 class="w3-border-bottom w3-padding-16">2023-2024 BagnUM Roster</h1>

<div class="w3-row-padding">
    {% for player in site.data.roster %}
    <div class="w3-col l3 m6 w3-margin-bottom">
        <div class="w3-card w3-white" style="border-radius:8px; overflow:hidden;">
            <!-- Captain Badge -->
            {% if player.captain %}
            <div class="w3-container w3-blue w3-center">
                <p style="margin:2px; font-size:10px; text-transform:uppercase;">Captain</p>
            </div>
            {% endif %}

            <div class="w3-display-container">
                <img src="{{ player.image }}" alt="{{ player.name }}" style="width:100%">
                <span class="w3-display-topleft w3-black w3-padding" style="opacity:0.8">#{{ player.number }}</span>
            </div>
            
            <div class="w3-container w3-center">
                <h4><b>{{ player.name }}</b></h4>
                <p class="w3-opacity">{{ player.position }} | {{ player.year }}</p>
                <p class="w3-small"><i>{{ player.bio }}</i></p>
            </div>
        </div>
    </div>
    {% endfor %}
</div>