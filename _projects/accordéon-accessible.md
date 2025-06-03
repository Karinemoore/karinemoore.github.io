---
layout: default
title: Accordéon accessible
---

<section class="container mx-auto py-20 max-w-4xl px-4">
  <h1 class="text-4xl font-bold mb-6">Accordéon accessible</h1>
  <p class="text-lg text-gray-700 mb-10 max-w-[75ch]">
    Ce composant accordéon est conçu pour être totalement accessible au clavier et aux lecteurs d'écran. Il utilise les attributs ARIA et une logique JavaScript légère pour garantir une expérience utilisateur inclusive.
  </p>

  <!-- Aperçu du composant -->
  <div data-accordion class="space-y-4 mb-12">
    <div>
      <h2>
        <button
          data-accordion-trigger
          aria-expanded="false"
          aria-controls="panel1"
          id="accordion1"
          class="w-full text-left text-xl font-semibold p-4 bg-gray-100 rounded hover:bg-gray-200 transition"
        >
          Qu'est-ce qu'un accordéon accessible ?
        </button>
      </h2>
      <div
        id="panel1"
        role="region"
        aria-labelledby="accordion1"
        hidden
        class="p-4 border border-t-0 border-gray-200 rounded-b"
      >
        <p>
          Un accordéon accessible permet de naviguer à l’aide du clavier, et informe correctement les technologies d’assistance de son état ouvert ou fermé.
        </p>
      </div>
    </div>

    <div>
      <h2>
        <button
          data-accordion-trigger
          aria-expanded="false"
          aria-controls="panel2"
          id="accordion2"
          class="w-full text-left text-xl font-semibold p-4 bg-gray-100 rounded hover:bg-gray-200 transition"
        >
          Comment ça fonctionne ?
        </button>
      </h2>
      <div
        id="panel2"
        role="region"
        aria-labelledby="accordion2"
        hidden
        class="p-4 border border-t-0 border-gray-200 rounded-b"
      >
        <p>
          Grâce à une structure HTML adaptée et une logique JavaScript simple, chaque bouton contrôle l’ouverture de son panneau.
        </p>
      </div>
    </div>
  </div>

  <!-- Section code (sans bouton copier) -->
  <div class="bg-gray-50 p-6 rounded-lg shadow overflow-x-auto">
    <pre class="text-sm text-gray-800"><code>&lt;div data-accordion&gt;
  &lt;h2&gt;
    &lt;button
      data-accordion-trigger
      aria-expanded="false"
      aria-controls="panel1"
      id="accordion1"
    &gt;
      Titre
    &lt;/button&gt;
  &lt;/h2&gt;
  &lt;div id="panel1" role="region" aria-labelledby="accordion1" hidden&gt;
    Contenu
  &lt;/div&gt;
&lt;/div&gt;</code></pre>
  </div>
</section>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const accordions = document.querySelectorAll('[data-accordion]');
    accordions.forEach(accordion => {
      const triggers = accordion.querySelectorAll('[data-accordion-trigger]');
      triggers.forEach(trigger => {
        trigger.addEventListener('click', () => {
          const expanded = trigger.getAttribute('aria-expanded') === 'true';
          trigger.setAttribute('aria-expanded', !expanded);
          const panel = document.getElementById(trigger.getAttribute('aria-controls'));
          if (panel) panel.hidden = expanded;
        });
      });
    });
  });
</script>
