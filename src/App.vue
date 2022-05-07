
<template>
  <HelloWorld msg="Sorts :" />

  <h1
    class="
      text-4xl
      tracking-tight
      font-extrabold
      text-gray-900
      sm:text-5xl
      md:text-6xl
    "
  >
    <span class="block xl:inline">WikiSorts</span>
  </h1>
  <div>
    <div class="flex justify-center m-8">
      <div class="hidden w-3/4 sm:block">
        <nav
          class="relative z-0 rounded-lg shadow flex divide-x divide-gray-200"
          aria-label="Tabs"
        >
          <!-- Current: "text-gray-900", Default: "text-gray-500 hover:text-gray-700" -->
          <!--Permet la séléction de l'onglet à afficher -->
          <button
            v-on:click="ongletAccueil"
            class="
              text-gray-900
              rounded-l-lg
              group
              relative
              min-w-0
              flex-1
              overflow-hidden
              bg-white
              py-4
              px-4
              text-sm
              font-medium
              text-center
              hover:bg-gray-50
              focus:z-10
            "
            aria-current="page"
          >
            <span>Accueil</span>
            <span
              aria-hidden="true"
              :class="[
                ongletCourant === 'accueil' ? activeClass : nonActiveClass,
                'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5',
              ]"
            ></span>
          </button>

          <button
            v-on:click="ongletRecherche"
            class="
              text-gray-900
              hover:text-gray-700
              group
              relative
              min-w-0
              flex-1
              overflow-hidden
              bg-white
              py-4
              px-4
              text-sm
              font-medium
              text-center
              hover:bg-gray-50
              focus:z-10
            "
          >
            Recherche
            <span
              aria-hidden="true"
              :class="[
                ongletCourant === 'recherche' ? activeClass : nonActiveClass,
                'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5',
              ]"
            ></span>
          </button>

          <button
            v-on:click="ongletStats"
            class="
              text-gray-900
              hover:text-gray-700
              group
              relative
              min-w-0
              flex-1
              overflow-hidden
              bg-white
              py-4
              px-4
              text-sm
              font-medium
              text-center
              hover:bg-gray-50
              focus:z-10
            "
          >
            <span>Stats</span>
            <span
              aria-hidden="true"
              :class="[
                ongletCourant === 'stats' ? activeClass : nonActiveClass,
                'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5',
              ]"
            ></span>
          </button>

          <button
            v-on:click="ongletConfiguration"
            class="
              text-gray-900
              hover:text-gray-700
              rounded-r-lg
              group
              relative
              min-w-0
              flex-1
              overflow-hidden
              bg-white
              py-4
              px-4
              text-sm
              font-medium
              text-center
              hover:bg-gray-50
              focus:z-10
            "
          >
            <span>Configuration</span>
            <span
              aria-hidden="true"
              :class="[
                ongletCourant === 'configuration'
                  ? activeClass
                  : nonActiveClass,
                'bg-indigo-500 absolute inset-x-0 bottom-0 h-0.5',
              ]"
            ></span>
          </button>
        </nav>
      </div>
    </div>
    <!--Permet d'afficher l'onglet souhaité -->
    
    <div v-if="ongletCourant === 'stats'">
      <spellStats :data="data" />
    </div>
    <div v-else-if="ongletCourant === 'recherche'">
      <ongletRecherche :data="data" />
    </div>
    <div v-else-if="ongletCourant === 'configuration'">
      <ongletConfiguration />
    </div>
    <div v-else>
      <ongletAccueil :data="data" />
    </div>
  </div>
</template>

<script>
import ongletConfiguration from "./components/formConfiguration.vue";
import ongletAccueil from "./components/formAccueil.vue";
import ongletRecherche from "./components/formSpellSearch.vue";
import spellStats from "./components/formSpellStats.vue";
import data from "./assets/data.min.js"; // Lien vers toutes les données

export default {
  name: "App",
  components: {
    spellStats,
    ongletAccueil,
    ongletConfiguration,
    ongletRecherche,
  },
  data: function () {
    return {
      data,
      ongletCourant: "accueil",
      activeClass: "bg-indigo-500",
      nonActiveClass: "bg-transparent",
      config: this.initConfig()
    };
  },
  methods: {
    //méthodes permettants d'affecter une valeur à this.ongletCourant dans le but d'afficher l'onglet correspondant
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
    initConfig() {
      let config = JSON.parse(localStorage.getItem("config"));
      if (!config) {
        config = {ecole: true, branche: true, classes: true, niveau: true};
        localStorage.setItem("config", JSON.stringify(config));
      }
      return config;
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
