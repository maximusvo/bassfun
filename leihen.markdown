---
layout: default
title: Leihen
permalink: /leihen/
description: >-
  Alle Leihpakete auf einen Blick: Starter, Club, Festival und DJ-Service.
  Hochwertige RCF-PA-Technik für Events in Brandenburg – Paket wählen und anfragen.
---

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "ItemList",
  "itemListElement": [
    {% for package in site.data.packages %}
    {
      "@type": "Product",
      "position": {{ forloop.index }},
      "name": {{ package.name | jsonify }},
      "description": {{ package.description | strip_newlines | strip | jsonify }},
      "url": "{{ site.url }}{{ '/anfrage/' | relative_url }}?paket={{ package.id }}"
      {% if package.price_from %},
      "offers": {
        "@type": "Offer",
        "priceCurrency": "EUR",
        "price": {{ package.price_from }},
        "availability": "https://schema.org/InStock",
        "url": "{{ site.url }}{{ '/anfrage/' | relative_url }}?paket={{ package.id }}"
      }
      {% endif %}
    }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ]
}
</script>

<section class="hero" style="padding: 90px 0 60px;">
  <div class="wrap">
    <div class="hero-content">
      <span class="eyebrow">Leihpakete</span>
      <h1>Wähle dein Set</h1>
      <p class="lead">
        Alle Pakete auf einen Blick. Klicke auf „Anfragen“ – dein Paket ist
        im Formular direkt vorausgewählt.
      </p>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <div class="package-grid">
      {% for package in site.data.packages %}
      <div class="package-card{% if package.highlight %} is-highlight{% endif %}">
        {% if package.highlight %}<span class="package-badge">Beliebt</span>{% endif %}
        <h3>{{ package.name }}</h3>
        <p class="tagline">{{ package.tagline }}</p>

        <div class="package-meta">
          <span class="guests">{{ package.guests }}</span>
          <span class="price">{{ package.price }}</span>
        </div>

        <p>{{ package.description }}</p>

        <ul class="package-equipment">
          {% for item in package.equipment %}
          <li>{{ item }}</li>
          {% endfor %}
        </ul>

        <a href="{{ '/anfrage/' | relative_url }}?paket={{ package.id }}" class="btn btn-primary">Anfragen</a>
      </div>
      {% endfor %}
    </div>
  </div>
</section>

<section class="cta-band">
  <div class="wrap">
    <h2>Dein Event, deine Größe?</h2>
    <p>Nicht sicher, welches Paket passt? Schreib uns – wir beraten dich gern.</p>
    <a href="{{ '/anfrage/' | relative_url }}" class="btn btn-primary">Jetzt anfragen</a>
  </div>
</section>
