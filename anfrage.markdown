---
layout: default
title: Anfrage
permalink: /anfrage/
description: >-
  Frag dein Wunschpaket für den Lautsprecherverleih in Brandenburg unverbindlich
  per Mail an – schnell und unkompliziert, ganz ohne Registrierung.
---

<section class="hero" style="padding: 90px 0 60px;">
  <div class="wrap">
    <div class="hero-content">
      <span class="eyebrow">Anfrage</span>
      <h1>Paket anfragen</h1>
      <p class="lead">
        Fülle das Formular aus und klicke auf „Anfrage per Mail senden“.
        Es öffnet sich dein E-Mail-Programm mit einer vorausgefüllten Mail
        an uns – abschicken musst du sie selbst.
      </p>
    </div>
  </div>
</section>

<section style="padding-top:0;">
  <div class="wrap">
    <form class="form-card" id="anfrage-form">
      <div class="form-grid-2">
        <div class="form-row">
          <label for="vorname">Vorname</label>
          <input type="text" id="vorname" name="vorname" required>
        </div>
        <div class="form-row">
          <label for="nachname">Nachname</label>
          <input type="text" id="nachname" name="nachname" required>
        </div>
      </div>

      <div class="form-row">
        <label for="telefon">Telefonnummer</label>
        <input type="tel" id="telefon" name="telefon" required>
      </div>

      <div class="form-row">
        <label for="adresse">Adresse</label>
        <textarea id="adresse" name="adresse" rows="3" required placeholder="Straße, Hausnummer, PLZ, Ort"></textarea>
      </div>

      <div class="form-row">
        <label for="paket">Gebuchtes Paket</label>
        <select id="paket" name="paket" required>
          {% for package in site.data.packages %}
          <option value="{{ package.id }}">{{ package.name }} ({{ package.guests }})</option>
          {% endfor %}
        </select>
      </div>

      <button type="submit" class="btn btn-primary">Anfrage per Mail senden</button>

      <p class="form-note">
        Beim Klick öffnet sich dein Standard-E-Mail-Programm mit einer
        vorausgefüllten Nachricht an <strong>{{ site.email }}</strong>. Wir
        senden dabei nichts automatisch ab – du prüfst die Mail und
        schickst sie selbst.
      </p>

      <div class="form-status" id="form-status"></div>
    </form>
  </div>
</section>

<script>
(function () {
  var form = document.getElementById('anfrage-form');
  var paketSelect = document.getElementById('paket');
  var status = document.getElementById('form-status');
  var mailTo = {{ site.email | jsonify }};

  // Paket per Query-Parameter (?paket=id) vorauswählen, z.B. von /leihen/ aus
  var params = new URLSearchParams(window.location.search);
  var preselect = params.get('paket');
  if (preselect) {
    for (var i = 0; i < paketSelect.options.length; i++) {
      if (paketSelect.options[i].value === preselect) {
        paketSelect.selectedIndex = i;
        break;
      }
    }
  }

  form.addEventListener('submit', function (e) {
    e.preventDefault();

    var vorname = document.getElementById('vorname').value.trim();
    var nachname = document.getElementById('nachname').value.trim();
    var telefon = document.getElementById('telefon').value.trim();
    var adresse = document.getElementById('adresse').value.trim();
    var paketName = paketSelect.options[paketSelect.selectedIndex].text;

    var subject = 'Anfrage Verleihpaket: ' + paketName;
    var body = [
      'Hallo Bassfun-Team,',
      '',
      'ich möchte folgendes Paket anfragen:',
      '',
      'Vorname: ' + vorname,
      'Nachname: ' + nachname,
      'Telefonnummer: ' + telefon,
      'Adresse: ' + adresse,
      'Gebuchtes Paket: ' + paketName,
      '',
      'Viele Grüße'
    ].join('\n');

    var mailtoLink = 'mailto:' + encodeURIComponent(mailTo)
      + '?subject=' + encodeURIComponent(subject)
      + '&body=' + encodeURIComponent(body);

    window.location.href = mailtoLink;

    status.textContent = 'Dein E-Mail-Programm sollte sich jetzt geöffnet haben. Bitte prüfe die Mail und schicke sie ab.';
    status.classList.add('is-visible');
  });
})();
</script>
