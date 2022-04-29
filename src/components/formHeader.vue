<template>
  <div>
    <div>
      <button v-on:click="ongletRecherche">Accueil</button>
      <button v-on:click="ongletRecherche">Recherche</button>
      <button v-on:click="ongletStats">Stats</button>
      <button v-on:click="ongletConfiguration">Configuration</button>
    </div>
    <div v-if="ongletCourant === 'accueil'">
      <h1>Accueil</h1>
    </div>
    <div v-if="ongletCourant === 'stats'">
      <h1>Stats</h1>
    </div>
    <div v-if="ongletCourant === 'recherche'">
      <h1>Recherche</h1>
    </div>
    <div v-if="ongletCourant === 'configuration'">
      <h1>Configuration</h1>
    </div>
  </div>
</template>


<script>
export default {
  name: "menuHeader",
  data: function() {
    return {
      ongletCourant: "accueil"
    }
  },
  methods: {
    ongletRecherche() {
      alert("Recherche");
    },
    ongletStats() {
      console.log("Stats");
    },
    ongletConfiguration() {
      alert("Configuration");
    },
  },
};
</script>