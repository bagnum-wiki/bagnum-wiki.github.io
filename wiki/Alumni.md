---
title: Alumni & History
---

<style>
    .alumni-section { border-bottom: 2px solid #eee; margin-top: 50px; padding-bottom: 10px; color: #555; }
</style>

<div class="w3-container">
    <h1 class="w3-jumbo"><b>BagnUM Alumni</b></h1>
    <p class="w3-xlarge">Celebrating the players who built this program.</p>

    {% comment %} 
        1. Filter for only Alumni 
        2. Group them by their graduation year
        3. Sort so the newest alumni are at the top
    {% endcomment %}
    
    {% assign alumni_groups = site.data.roster | where: "alumni", true | group_by: "grad_year" | sort: "name" | reverse %}

    {% for year_group in alumni_groups %}
        <h2 class="alumni-section">Class of {{ year_group.name }}</h2>
        <div class="w3-row-padding">
            {% for player in year_group.items %}
                {% include player_card.html player=player %}
            {% endfor %}
        </div>
    {% endfor %}

</div>