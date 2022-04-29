
<template>
  <HelloWorld msg="Sorts :" />

        <h1 class="text-4xl tracking-tight font-extrabold text-gray-900 sm:text-5xl md:text-6xl">
          <span class="block xl:inline">Wiki des sorts</span>
        </h1>
<div>
<div class="flex justify-center m-8">
  <div class="hidden w-3/4 sm:block">
    <nav class="relative z-0 rounded-lg shadow flex divide-x divide-gray-200" aria-label="Tabs">
      <!-- Current: "text-gray-900", Default: "text-gray-500 hover:text-gray-700" -->
      <button v-on:click="ongletAccueil" class="text-gray-900 rounded-l-lg group relative min-w-0 flex-1 overflow-hidden bg-white py-4 px-4 text-sm font-medium text-center hover:bg-gray-50 focus:z-10" aria-current="page">
        <span>Accueil</span>
        <span aria-hidden="true" :class="[ongletCourant === 'accueil' ? activeClass : nonActiveClass, 'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5']"></span>
      </button>

      <button v-on:click="ongletRecherche" class="text-gray-900 hover:text-gray-700 group relative min-w-0 flex-1 overflow-hidden bg-white py-4 px-4 text-sm font-medium text-center hover:bg-gray-50 focus:z-10">
        Recherche
        <span aria-hidden="true" :class="[ongletCourant === 'recherche' ? activeClass : nonActiveClass, 'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5']"></span>
      </button>

      <button v-on:click="ongletStats" class="text-gray-900 hover:text-gray-700 group relative min-w-0 flex-1 overflow-hidden bg-white py-4 px-4 text-sm font-medium text-center hover:bg-gray-50 focus:z-10">
        <span>Stats</span>
        <span aria-hidden="true" :class="[ongletCourant === 'stats' ? activeClass : nonActiveClass, 'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5']"></span>
      </button>

      <button v-on:click="ongletConfiguration" class="text-gray-900 hover:text-gray-700 rounded-r-lg group relative min-w-0 flex-1 overflow-hidden bg-white py-4 px-4 text-sm font-medium text-center hover:bg-gray-50 focus:z-10">
        <span>Configuration</span>
        <span aria-hidden="true" :class="[ongletCourant === 'configuration' ? activeClass : nonActiveClass, 'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5']"></span>
      </button>
    </nav>
  </div>
</div>
    <div v-if="ongletCourant === 'accueil'">
      <h1>Accueil</h1>
    </div>
    <div v-if="ongletCourant === 'stats'">
      <spellStats :data="data" />
    </div>
    <div v-if="ongletCourant === 'recherche'">
      <checkBoxSelect @spellSearch="updateSearch" />
      <spellTable :data="data" />
    </div>
    <div v-if="ongletCourant === 'configuration'">
      <h1>Configuration</h1>
    </div>
  </div>

</template>

<script>

import spellTable from "./components/formTable.vue";
import checkBoxSelect from "./components/formCheckBoxSelect.vue";
import spellStats from "./components/formSpellStats.vue";
import data from "./assets/data.min.js"; // Lien vers toutes les données

export default {
  name: "App",
  components: {
    checkBoxSelect,
    spellStats,
    spellTable
  },
  data: function () {
    return { searchName: "", searchNameBox: "", data, ongletCourant: "accueil",
      activeClass: "bg-indigo-500", nonActiveClass: "bg-transparent" };
  },
  methods: {
    updateSearch(searchName, searchNameBox) {
      this.searchName = searchName;
      this.searchNameBox = searchNameBox;
    },
    ongletAccueil() {
      this.ongletCourant = "accueil";
    },
    ongletRecherche() {
      this.ongletCourant = "recherche";
    },
    ongletStats() {
      this.ongletCourant = "stats";
    },
    ongletConfiguration() {
      this.ongletCourant = "configuration";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table {
  margin-top: 20px;
  margin-left: auto;
  margin-right: auto;
}

.stats {
  width: 100%;
  border-collapse: collapse;
  border: 2px solid black;
}
th {
  padding: 5px;
}
</style>
