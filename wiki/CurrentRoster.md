---
title: Current Roster
---

<style>
    .player-card { transition: 0.3s; border-radius: 8px; overflow: hidden; margin-bottom: 20px; }
    .section-header { border-bottom: 2px solid #00274C; margin-top: 40px; padding-bottom: 10px; color: #00274C; }
</style>

<div class="w3-container">
    <h1 class="w3-jumbo"><b>BagnUM Roster</b></h1>

    {% comment %} 
      First, we filter out any Alumni so they don't show up on this page 
    {% endcomment %}
    {% assign active_players = site.data.roster | where: "alumni", false %}

    <!-- 1. CAPTAINS SECTION -->
    {% assign captains = active_players | where: "captain", true %}
    {% if captains.size > 0 %}
        <h2 class="section-header">⭐ Captains</h2>
        <div class="w3-row-padding">
            {% for player in captains %}
                {% include player-card.html player=player color="w3-indigo" %}
            {% endfor %}
        </div>
    {% endif %}

    {% comment %} 
      Now we filter for non-captains and group them by year 
    {% endcomment %}
    {% assign non_captains = active_players | where: "captain", false %}
    {% assign classes = "Grad Student,Senior,Junior,Sophomore,Freshman" | split: "," %}

    {% for class in classes %}
        {% assign class_players = non_captains | where: "year", class %}
        
        {% if class_players.size > 0 %}
            <h2 class="section-header">{{ class }}s</h2>
            <div class="w3-row-padding">
                {% for player in class_players %}
                    {% include player-card.html player=player color="w3-white" %}
                {% endfor %}
            </div>
        {% endif %}
    {% endfor %}

</div>