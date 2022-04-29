<template>
  <HelloWorld msg="Sorts :" />

  <h1>Wiki des sorts</h1>
  <div>
    <div>
      <button v-on:click="ongletAccueil">Accueil</button>
      <button v-on:click="ongletRecherche">Recherche</button>
      <button v-on:click="ongletStats">Stats</button>
      <button v-on:click="ongletConfiguration">Configuration</button>
    </div>
    <div v-if="ongletCourant === 'accueil'">
      <h1>Accueil</h1>
    </div>
    <div v-if="ongletCourant === 'stats'">
      <h1>Stats</h1>
      <spellStats :data="data" />
    </div>
    <div v-if="ongletCourant === 'recherche'">
      <h1>Recherche</h1>
      <checkBoxSelect @spellSearch="updateSearch" />
      <spellTable :spellSearch="spellSearch" />
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
    return { searchName: "", searchNameBox: "", data, ongletCourant: "accueil" };
  },
  computed: {
    spellSearch() {
      /*On récupère les data de la base JS qu'on importe,
        On filtre toutes les valeurs
        On encapsule chaque valeur de nom, ici 'spell[1]' dans une variable 'spell'
        Qui commence par les valeurs rentrés dans la zone de texte de l'input */
      console.log(this.searchNameBox);
      console.log(data);

      if (this.searchNameBox)
        return data.filter((spell) => spell[1].startsWith(this.searchName));
      else return [];
    },
    statistiqueSort() {
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        return value.length;
      } else return 0;
    },
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
