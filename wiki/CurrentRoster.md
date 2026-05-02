---
title: Current Roster
---

<style>
    .section-header { border-bottom: 2px solid #ddd; margin-top: 40px; padding-bottom: 10px; color: #333; text-transform: uppercase; letter-spacing: 1px; }
</style>

<div class="w3-container">
    <h1 class="w3-jumbo"><b>BagnUM Roster</b></h1>

    {% assign all_players = site.data.roster %}

    <!-- 1. CAPTAINS SECTION -->
    <h2 class="section-header">⭐ Captains</h2>
    <div class="w3-row-padding">
        {% for player in all_players %}
            {% if player.captain == true %}
                {% include player_card.html player=player %}
            {% endif %}
        {% endfor %}
    </div>

    <!-- 2. THE SQUAD (BY CLASS) -->
    {% assign classes = "Grad Student,Senior,Junior,Sophomore,Freshman" | split: "," %}

    {% for class in classes %}
        {% comment %} Check if there are players in this class who aren't captains {% endcomment %}
        <h2 class="section-header">{{ class }}s</h2>
        <div class="w3-row-padding">
            {% for player in all_players %}
                {% if player.year == class and player.captain != true and player.alumni != true %}
                    {% include player_card.html player=player %}
                {% endif %}
            {% endfor %}
        </div>
    {% endfor %}

</div>