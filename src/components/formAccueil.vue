<template>
  <div class="flex justify-center m-8">
    <section class="font-semibold">
      <h1>Bienvenue sur WikiSorts</h1>
      <p>WikiSorts est la plus grande blibliothèque de livre de Sorts.</p>
      <ul>
        <strong>Fonctionnalités disponibles :</strong>
        <li>Les Statistiques</li>
        <li>La Recherche</li>
        <li>La Configuration</li>
      </ul>
      <h3>Nombre total de livre : {{ data.length }}</h3>
    </section>
  </div>
  <table class="w-full divide-y divide-gray-300">
    <thead class="bg-gray-50">
      <tr>
        <th
          scope="col"
          class="
            whitespace-nowrap
            py-3.5
            pt-0
            pl-4
            pr-3
            text-center text-sm
            font-semibold
            text-gray-900
            sm:pl-6
          "
        >
          Livre
        </th>
        <th
          scope="col"
          class="
            whitespace-nowrap
            px-2
            py-3.5
            pt-0
            text-center text-sm
            font-semibold
            text-gray-900
          "
        >
          Nom
        </th>
        <th
          scope="col"
          class="
            whitespace-nowrap
            px-2
            py-3.5
            pt-0
            text-center text-sm
            font-semibold
            text-gray-900
          "
        >
          Ecole
        </th>
        <th
          scope="col"
          class="
            whitespace-nowrap
            px-2
            py-3.5
            pt-0
            text-center text-sm
            font-semibold
            text-gray-900
          "
        >
          Branche
        </th>
        <th
          scope="col"
          class="
            whitespace-nowrap
            px-2
            py-3.5
            pt-0
            text-center text-sm
            font-semibold
            text-gray-900
          "
        >
          Classe
        </th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-200 bg-white">
      <tr class="spellTab" v-for="spellFor in data" :key="spellFor[1]">
        <!--On appel l'élément spell de spellView et on lui donne la valeur de spellFor pour qu'il travaille avec -->
        <spellView :spell="spellFor" />
      </tr>
    </tbody>
  </table>
</template>


<script>
import spellView from "./formSpellView.vue";

export default {
  name: "ongletAccueil",
  props: ["data"],
  components: {
    spellView,
  },
};
</script>

<style>
section {
  text-align: center;
}

h1 {
  font-size: 30px;
}

h3 {
  text-decoration-line: underline;
}

strong {
  font-size: 20px;
}

ul {
  list-style-type: disc;
  list-style-position: inside;
  text-align: left;
}

li {
  margin-left: 6px;
}
</style>