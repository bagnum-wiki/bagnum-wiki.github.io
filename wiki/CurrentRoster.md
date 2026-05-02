---
title: Current Roster
---

<style>
    .player-card { transition: 0.3s; border-radius: 8px; overflow: hidden; margin-bottom: 20px; border: 1px solid #eee; }
    .section-header { border-bottom: 2px solid #00274C; margin-top: 40px; padding-bottom: 10px; color: #00274C; text-transform: uppercase; letter-spacing: 1px; }
</style>

<div class="w3-container">
    <h1 class="w3-jumbo"><b>BagnUM Roster</b></h1>

    {% comment %} Grab the data safely {% endcomment %}
    {% assign all_players = site.data.roster %}

    <!-- 1. CAPTAINS SECTION -->
    <h2 class="section-header">⭐ Captains</h2>
    <div class="w3-row-padding">
        {% for player in all_players %}
            {% if player.captain == true %}
                {% include player_card.html player=player color="w3-indigo" %}
            {% endif %}
        {% endfor %}
    </div>

    <!-- 2. THE SQUAD (BY CLASS) -->
    {% assign classes = "Grad Student,Senior,Junior,Sophomore,Freshman" | split: "," %}

    {% for class in classes %}
        {% comment %} Count if there are any non-captains in this class before showing header {% endcomment %}
        <h2 class="section-header">{{ class }}s</h2>
        <div class="w3-row-padding">
            {% for player in all_players %}
                {% if player.year == class and player.captain != true and player.alumni != true %}
                    {% include player_card.html player=player color="w3-white" %}
                {% endif %}
            {% endfor %}
        </div>
    {% endfor %}

</div>