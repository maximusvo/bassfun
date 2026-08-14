---
layout: default
title: Start
---

<section class="hero">
  <div class="wrap">
    <div class="hero-content">
      <span class="eyebrow">PA-Verleih Brandenburg</span>
      <h1>Sound, der<br>trägt.</h1>
      <p class="lead">
        Wir verleihen hochwertige Aktivlautsprecher für Partys, Hochzeiten
        und Events – druckvoller Bass, klarer Sound, unkompliziert gebucht.
      </p>
      <div class="hero-actions">
        <a href="{{ '/leihen/' | relative_url }}" class="btn btn-primary">Leihpakete ansehen</a>
        <a href="{{ '/anfrage/' | relative_url }}" class="btn btn-outline">Jetzt anfragen</a>
      </div>

      <div class="hero-stats">
        <div>
          <div class="stat-num">4</div>
          <div class="stat-label">Verleihpakete</div>
        </div>
        <div>
          <div class="stat-num">400+</div>
          <div class="stat-label">Gäste möglich</div>
        </div>
        <div>
          <div class="stat-num">100%</div>
          <div class="stat-label">Bassdruck</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="section-alt">
  <div class="wrap">
    <div class="showcase-grid">
      <img
        src="{{ '/assets/img/club-set.svg' | relative_url }}"
        alt="Zwei PA-Stacks aus je einem RCF SUB 8003-AS MK3 Subwoofer und einem RCF ART 935-A Topteil in einer Club-Atmosphäre"
        class="showcase-image"
        loading="lazy">

      <div>
        <span class="eyebrow">Unser Equipment</span>
        <h2>Festivalsound, der ankommt</h2>
        <p>
          Zwei Stacks aus je einem kraftvollen Subwoofer und einem klaren
          Topteil sorgen für satten Bass und druckvolle Höhen bis in die
          letzte Reihe – genau das richtige Setup für Open-Airs, große
          Bühnen und Festivals.
        </p>
        <ul class="package-equipment">
          <li>2x RCF SUB 8003-AS MK3</li>
          <li>2x RCF ART 935-A</li>
        </ul>
        <a href="{{ '/anfrage/' | relative_url }}?paket=festival" class="btn btn-primary">Dieses Set anfragen</a>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Warum Bassfun</span>
      <h2>Technik, auf die du dich verlassen kannst</h2>
    </div>

    <div class="feature-grid">
      <div class="feature-card">
        <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="4"/><circle cx="12" cy="12" r="0.8" fill="currentColor"/></svg>
        <h3>Profi-Equipment</h3>
        <p>Aktivlautsprecher und Subwoofer für satten Bass und klaren Sound – bei jeder Lautstärke.</p>
      </div>
      <div class="feature-card">
        <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18M9 3v18"/></svg>
        <h3>Passendes Paket</h3>
        <p>Vom privaten Geburtstag bis zum Open-Air – wir haben das passende Set für deine Gästezahl.</p>
      </div>
      <div class="feature-card">
        <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><path d="M3 12l4-8h10l4 8-4 8H7z"/></svg>
        <h3>Faire Preise</h3>
        <p>Transparente Tagespreise ohne versteckte Kosten – auf Wunsch inklusive Lieferung.</p>
      </div>
      <div class="feature-card">
        <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><path d="M12 3v18M5 8l7-5 7 5M5 16l7 5 7-5"/></svg>
        <h3>Persönlicher Service</h3>
        <p>Kurze Wege, direkte Absprache und auf Wunsch Auf- und Abbau durch uns.</p>
      </div>
    </div>
  </div>
</section>

<section class="section-alt">
  <div class="wrap">
    <div class="section-head">
      <span class="eyebrow">Leihpakete</span>
      <h2>Für jede Veranstaltung das richtige Set</h2>
    </div>

    <div class="package-grid">
      {% for package in site.data.packages limit: 3 %}
      <div class="package-card{% if package.highlight %} is-highlight{% endif %}">
        {% if package.highlight %}<span class="package-badge">Beliebt</span>{% endif %}
        <h3>{{ package.name }}</h3>
        <p class="tagline">{{ package.tagline }}</p>
        <div class="package-meta">
          <span class="guests">{{ package.guests }}</span>
          <span class="price">{{ package.price }}</span>
        </div>
        <a href="{{ '/anfrage/' | relative_url }}?paket={{ package.id }}" class="btn btn-outline">Anfragen</a>
      </div>
      {% endfor %}
    </div>

    <p class="text-center" style="margin-top:2.5em;">
      <a href="{{ '/leihen/' | relative_url }}" class="btn btn-primary">Alle Leihpakete ansehen</a>
    </p>
  </div>
</section>

<section class="cta-band">
  <div class="wrap">
    <h2>Bereit für deinen Sound?</h2>
    <p>Wähle dein Paket und schick uns deine Anfrage – wir melden uns schnellstmöglich zurück.</p>
    <a href="{{ '/anfrage/' | relative_url }}" class="btn btn-primary">Jetzt anfragen</a>
  </div>
</section>
