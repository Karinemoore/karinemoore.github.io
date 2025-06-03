---
layout: project
title: Accordéon accessible
# image: '../assets/images/projets.jpg'
category: Dev
tags:
  - Accessibility
---

<div class="max-w-2xl mx-auto my-8" id="accessible-accordion">
  <h2 id="accordion-title" class="text-2xl font-bold mb-4">Exemple d'accordéon accessible</h2>

  {% assign sections = "Présentation|Nunc eleifend dolor vitae lorem dictum rhoncus. Proin id pulvinar turpis, et eleifend quam.,Détails techniques|Nulla odio nisl, sagittis et tortor non, aliquam vestibulum neque. Etiam eu venenatis sem. Morbi ex turpis, dictum sit amet commodo eget, egestas sed felis. In a purus et lacus mollis sagittis.,Accessibilité|Accordéon respectant les critères d’accessibilité WCAG avec navigation clavier, attributs ARIA, et indication d’état." | split: "," %}
  {% for section in sections %}
    {% assign parts = section | split: "|" %}
    {% assign index = forloop.index %}
    {% assign title = parts[0] %}
    {% assign content = parts[1] %}

  <div class="border-b border-gray-300">
    <button
      class="accordion-header flex w-full items-center justify-between py-3 px-4 font-semibold hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#99bcc1] transition"
      aria-expanded="false"
      aria-controls="section{{ index }}"
      id="accordion-header-{{ index }}"
    >
      <span>{{ title }}</span>
      <svg class="accordion-icon w-5 h-5 transition-transform duration-200 transform" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
        <path fill-rule="evenodd" d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4.24 4.25a.75.75 0 01-1.06 0L5.21 8.29a.75.75 0 01.02-1.08z" clip-rule="evenodd" />
      </svg>
    </button>
    <div
      id="section{{ index }}"
      role="region"
      aria-labelledby="accordion-header-{{ index }}"
      class="accordion-panel hidden px-4 pb-4 text-gray-700"
    >
      <p>{{ content }}</p>
    </div>
  </div>
  {% endfor %}
</div>

<!-- Fenêtre de code à copier -->
<div class="max-w-2xl mx-auto mt-12 bg-gray-100 rounded-lg shadow p-4 relative" role="region" aria-label="Extrait de code">
  <button
    onclick="copyAccordionCode(this)"
    class="absolute top-2 right-2 text-sm bg-[#99bcc1] text-white px-3 py-1 rounded hover:bg-[#82a3a8] focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#99bcc1]"
    aria-label="Copier le code"
  >
    Copier
  </button>
  <pre class="overflow-x-auto text-sm leading-relaxed"><code id="accordion-code">
&lt;div id="accessible-accordion"&gt;
  &lt;button aria-expanded="false" aria-controls="section1"&gt;...&lt;/button&gt;
  &lt;div id="section1" role="region" aria-labelledby="accordion-header-1"&gt;
    &lt;p&gt;Contenu...&lt;/p&gt;
  &lt;/div&gt;
&lt;/div&gt;
  </code></pre>
</div>

<!-- JS: Accordéon + Copier -->
<script>
  document.querySelectorAll('#accessible-accordion .accordion-header').forEach(button => {
    button.addEventListener('click', () => {
      const expanded = button.getAttribute('aria-expanded') === 'true';
      const contentId = button.getAttribute('aria-controls');
      const content = document.getElementById(contentId);
      const icon = button.querySelector('.accordion-icon');

      document.querySelectorAll('#accessible-accordion .accordion-header').forEach(btn => {
        btn.setAttribute('aria-expanded', 'false');
        btn.querySelector('.accordion-icon').classList.remove('rotate-180');
      });
      document.querySelectorAll('#accessible-accordion .accordion-panel').forEach(panel => {
        panel.classList.add('hidden');
      });

      if (!expanded) {
        button.setAttribute('aria-expanded', 'true');
        content.classList.remove('hidden');
        icon.classList.add('rotate-180');
      }
    });
  });

  function copyAccordionCode(button) {
    const code = document.getElementById("accordion-code").innerText;
    navigator.clipboard.writeText(code).then(() => {
      const original = button.innerText;
      button.innerText = "Copié !";
      setTimeout(() => button.innerText = original, 2000);
    });
  }
</script>

<style>
  .accordion-icon.rotate-180 {
    transform: rotate(180deg);
  }
</style>
