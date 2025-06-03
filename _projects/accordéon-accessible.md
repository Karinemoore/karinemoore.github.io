---
layout: project
title: "Accordéon accessible"
description: "Composant d’accordéon conforme aux standards d’accessibilité ARIA."
---

<section class="max-w-3xl mx-auto px-4 py-16">
  <h1 class="text-3xl font-bold mb-4">Accordéon accessible</h1>
  <p class="text-gray-700 mb-8">
    Un composant web d’accordéon 100% accessible, respectant les recommandations du W3C. Conçu pour être inclusif, léger, et facile à intégrer.
  </p>

  <img src="/assets/images/accordeon-demo.png" alt="Démonstration de l'accordéon" class="rounded-xl shadow mb-8">

  <h2 class="text-xl font-semibold mb-2">Contexte</h2>
  <p class="text-gray-700 mb-6">
    Dans le cadre de mon apprentissage de l’accessibilité numérique, j’ai voulu concevoir un accordéon entièrement utilisable au clavier, avec un rôle ARIA correct et une navigation intuitive pour les technologies d’assistance.
  </p>

  <h2 class="text-xl font-semibold mb-2">Démarche</h2>
  <ul class="list-disc list-inside text-gray-700 mb-6">
    <li>Structure HTML sémantique</li>
    <li>Rôles ARIA : <code>aria-expanded</code>, <code>aria-controls</code>, etc.</li>
    <li>Navigation clavier fluide (tabulation, flèches…)</li>
    <li>Design simple et responsive avec Tailwind CSS</li>
  </ul>

  <h2 class="text-xl font-semibold mb-4">Démo interactive</h2>
  <div data-accordion class="space-y-4 mb-10">
    <div>
      <h3>
        <button
          data-accordion-trigger
          aria-expanded="false"
          aria-controls="panel1"
          id="accordion1"
          class="w-full text-left text-lg font-semibold p-4 bg-gray-100 rounded hover:bg-gray-200 transition"
        >
          Qu’est-ce qu’un accordéon accessible ?
        </button>
      </h3>
      <div
        id="panel1"
        role="region"
        aria-labelledby="accordion1"
        hidden
        class="p-4 border border-t-0 border-gray-200 rounded-b"
      >
        <p>
          Un accordéon accessible permet de naviguer à l’aide du clavier et informe correctement les technologies d’assistance de son état ouvert ou fermé.
        </p>
      </div>
    </div>

    <div>
      <h3>
        <button
          data-accordion-trigger
          aria-expanded="false"
          aria-controls="panel2"
          id="accordion2"
          class="w-full text-left text-lg font-semibold p-4 bg-gray-100 rounded hover:bg-gray-200 transition"
        >
          Comment ça fonctionne ?
        </button>
      </h3>
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

  <h2 class="text-xl font-semibold mb-2">Code HTML</h2>
  <div class="bg-gray-50 p-6 rounded shadow mb-10 overflow-x-auto">
    <pre class="text-sm text-gray-800"><code>&lt;div data-accordion&gt;
  &lt;h3&gt;
    &lt;button
      data-accordion-trigger
      aria-expanded="false"
      aria-controls="panel1"
      id="accordion1"
    &gt;
      Titre
    &lt;/button&gt;
  &lt;/h3&gt;
  &lt;div id="panel1" role="region" aria-labelledby="accordion1" hidden&gt;
    Contenu
  &lt;/div&gt;
&lt;/div&gt;</code></pre>
  </div>

  <h2 class="text-xl font-semibold mb-2">Ce que j’ai appris</h2>
  <p class="text-gray-700">
    Ce projet m’a permis de renforcer mes compétences en accessibilité et d’approfondir les techniques d’implémentation ARIA. Je l’ai conçu pour être réutilisable dans de futurs projets.
  </p>
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
