---
layout: default
title: ESP32 & M5Stack — Tutorial
---

<style>
body { background: #0d0d0d; color: #c9d1d9; font-family: 'Courier New', monospace; }
.hero { border: 1px solid #30e630; border-radius: 6px; padding: 2rem 2rem 1.6rem; margin: 2rem 0 2.5rem; }
.hero-dots { font-size: 10px; color: #30e630; letter-spacing: 6px; margin-bottom: 12px; }
.hero-title { font-size: 2rem; color: #30e630; letter-spacing: 2px; margin-bottom: 6px; }
.hero-sub { color: #8b949e; font-size: 0.95rem; line-height: 1.6; margin-bottom: 1.2rem; }
.hero-prompt { color: #30e630; font-size: 0.85rem; opacity: 0.7; }
.hero-prompt span { opacity: 1; color: #c9d1d9; }
.badges { display: flex; flex-wrap: wrap; gap: 8px; margin: 1.5rem 0 2rem; }
.badge { font-size: 0.75rem; padding: 4px 12px; border-radius: 20px; border: 1px solid; font-family: 'Courier New', monospace; }
.badge-green  { border-color: #30e630; color: #30e630; }
.badge-blue   { border-color: #58a6ff; color: #58a6ff; }
.badge-yellow { border-color: #e3b341; color: #e3b341; }
.badge-gray   { border-color: #8b949e; color: #8b949e; }
.section-title { color: #30e630; font-size: 0.8rem; letter-spacing: 3px; text-transform: uppercase; border-bottom: 1px solid #21262d; padding-bottom: 8px; margin: 2.5rem 0 1.2rem; }
.tutorial-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 16px; margin-bottom: 2rem; }
.tutorial-card { border: 1px solid #21262d; border-radius: 6px; padding: 1.2rem; background: #161b22; text-decoration: none; color: inherit; display: block; transition: border-color 0.2s; }
.tutorial-card:hover { border-color: #30e630; text-decoration: none; }
.card-tag { font-size: 0.7rem; color: #30e630; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 6px; }
.card-title { color: #e6edf3; font-size: 1rem; font-weight: bold; margin: 0 0 6px; }
.card-desc { color: #8b949e; font-size: 0.82rem; line-height: 1.5; margin: 0 0 12px; }
.card-meta { display: flex; gap: 12px; font-size: 0.75rem; color: #8b949e; }
.card-meta span { color: #30e630; }
.empty-state { border: 1px dashed #21262d; border-radius: 6px; padding: 2rem; text-align: center; color: #8b949e; font-size: 0.85rem; grid-column: 1 / -1; }
.empty-state code { color: #30e630; }
.info-box { border: 1px solid #21262d; border-left: 3px solid #30e630; border-radius: 0 6px 6px 0; padding: 1rem 1.2rem; background: #161b22; font-size: 0.85rem; color: #8b949e; line-height: 1.8; margin: 1rem 0; }
.info-box code { color: #30e630; background: transparent; }
.footer { border-top: 1px solid #21262d; margin-top: 3rem; padding-top: 1.2rem; font-size: 0.78rem; color: #8b949e; display: flex; justify-content: space-between; flex-wrap: wrap; gap: 8px; }
.footer a { color: #58a6ff; text-decoration: none; }
</style>

<div class="hero">
  <div class="hero-dots">● ● ●</div>
  <div class="hero-title">ESP32 &amp; M5Stack</div>
  <div class="hero-sub">
    Tutorial pratici per studenti — dalla configurazione dell'ambiente<br>
    ai progetti completi con sensori, display e connettività.
  </div>
  <div class="hero-prompt">$ git clone <span>https://github.com/TUOUSERNAME/esp32-tutorials.git</span></div>
</div>

<div class="badges">
  <span class="badge badge-green">ESP32</span>
  <span class="badge badge-green">M5Stack</span>
  <span class="badge badge-green">M5Stamp</span>
  <span class="badge badge-green">M5StickC</span>
  <span class="badge badge-blue">Arduino IDE</span>
  <span class="badge badge-blue">PlatformIO</span>
  <span class="badge badge-yellow">C++</span>
  <span class="badge badge-gray">Livello: base → intermedio</span>
</div>

<div class="section-title">// tutorial disponibili</div>

<div class="tutorial-grid">
  {% assign tutorials = site.tutorial | sort: "order" %}
  {% if tutorials.size > 0 %}
    {% for t in tutorials %}
    <a class="tutorial-card" href="{{ t.url | relative_url }}">
      <div class="card-tag">{{ t.device | default: "ESP32" }}</div>
      <div class="card-title">{{ t.title }}</div>
      <div class="card-desc">{{ t.description | default: "" }}</div>
      <div class="card-meta">
        <span>⏱</span> {{ t.duration | default: "—" }} &nbsp;
        <span>★</span> {{ t.difficulty | default: "⭐☆☆☆☆" }}
      </div>
    </a>
    {% endfor %}
  {% else %}
    <div class="empty-state">
      Nessun tutorial ancora.<br>
      Crea un file nella cartella <code>_tutorial/</code> con il front matter corretto<br>
      e apparirà automaticamente qui.
    </div>
  {% endif %}
</div>

<div class="info-box">
  <strong style="color:#e6edf3">Come aggiungere un tutorial →</strong><br>
  Crea un file <code>_tutorial/nome-progetto.md</code> con questo front matter:<br><br>
  <code>---</code><br>
  <code>layout: default</code><br>
  <code>title: "Titolo del tutorial"</code><br>
  <code>description: "Breve descrizione"</code><br>
  <code>device: "M5Stack Core2"</code><br>
  <code>duration: "30 min"</code><br>
  <code>difficulty: "⭐⭐☆☆☆"</code><br>
  <code>order: 1</code><br>
  <code>---</code>
</div>

<div class="section-title">// risorse utili</div>

<div class="info-box">
  <a href="https://docs.m5stack.com/" style="color:#58a6ff">docs.m5stack.com</a> — documentazione ufficiale M5Stack<br>
  <a href="https://randomnerdtutorials.com/esp32/" style="color:#58a6ff">randomnerdtutorials.com/esp32</a> — guide pratiche ESP32<br>
  <a href="https://docs.espressif.com/projects/arduino-esp32/en/latest/" style="color:#58a6ff">docs.espressif.com</a> — Arduino Core per ESP32<br>
  <a href="https://community.m5stack.com/" style="color:#58a6ff">community.m5stack.com</a> — forum ufficiale M5Stack
</div>

<div class="footer">
  <span>Progetto didattico — licenza CC BY-SA 4.0</span>
  <span><a href="https://github.com/TUOUSERNAME/esp32-tutorials">Vedi su GitHub →</a></span>
</div>
