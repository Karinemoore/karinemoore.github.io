---
layout: project
title: Accordéon accessible
image: 'https://picsum.photos/900/400'
category: Dev
tags:
  - Accessibility
---

<div class="max-w-2xl mx-auto my-8" id="accessible-accordion">
  <h2 id="accordion-title" class="text-2xl font-bold mb-4">Exemple d'accordéon accessible</h2>

  <div class="border-b border-gray-300">
    <button
      class="w-full text-left py-3 px-4 font-semibold hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#99bcc1]"
      aria-expanded="false"
      aria-controls="section1"
      id="accordion-header-1"
    >
      Section 1 : Présentation
    </button>
    <div
      id="section1"
      role="region"
      aria-labelledby="accordion-header-1"
      class="hidden px-4 pb-4 text-gray-700"
    >
      <p>Nunc eleifend dolor vitae lorem dictum rhoncus. Proin id pulvinar turpis, et eleifend quam.</p>
    </div>
  </div>

  <div class="border-b border-gray-300">
    <button
      class="w-full text-left py-3 px-4 font-semibold hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#99bcc1]"
      aria-expanded="false"
      aria-controls="section2"
      id="accordion-header-2"
    >
      Section 2 : Détails techniques
    </button>
    <div
      id="section2"
      role="region"
      aria-labelledby="accordion-header-2"
      class="hidden px-4 pb-4 text-gray-700"
    >
      <p>Nulla odio nisl, sagittis et tortor non, aliquam vestibulum neque. Etiam eu venenatis sem. Morbi ex turpis, dictum sit amet commodo eget, egestas sed felis. In a purus et lacus mollis sagittis.</p>
    </div>
  </div>

  <div class="border-b border-gray-300">
    <button
      class="w-full text-left py-3 px-4 font-semibold hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-[#99bcc1]"
      aria-expanded="false"
      aria-controls="section3"
      id="accordion-header-3"
    >
      Section 3 : Accessibilité
    </button>
    <div
      id="section3"
      role="region"
      aria-labelledby="accordion-header-3"
      class="hidden px-4 pb-4 text-gray-700"
    >
      <p>Accordéon respectant les critères d’accessibilité WCAG avec navigation clavier, attributs ARIA, et indication d’état.</p>
    </div>
  </div>
</div>

<script>
  document.querySelectorAll('#accessible-accordion button').forEach(button => {
    button.addEventListener('click', () => {
      const expanded = button.getAttribute('aria-expanded') === 'true';
      const content = document.getElementById(button.getAttribute('aria-controls'));

      button.setAttribute('aria-expanded', !expanded);
      content.classList.toggle('hidden');
    });
  });
</script>
