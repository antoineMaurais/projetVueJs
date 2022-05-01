<template>
  <searchBar @updateSearch="search => {
    this.recherche = search
    spellSearch()
    }" />
  <checkBoxSelect @eventOptionSelected="optionSelected($event)" />
  <h3>Nombre total de sorts trouvés: {{ spellData.length }}</h3>
  <formTable :spellAfficher="spellData" :key="spellData" />
</template>

<script>
import formTable from "./formTable.vue";
import searchBar from "./formSearchBar";
//import checkBoxSearchName from "./formCheckBoxSearchName.vue";
import checkBoxSelect from "./formCheckBoxSelect.vue";


export default {
  name: "ongletRecherche",
  props: ["data"],
  components: {
    formTable,
    checkBoxSelect,
    searchBar
  },
  data: function () {
    return {
      searchName: "",
      searchNameBox: "",
      spellData: this.data,
      ecoleListe: {option: ""},
      brancheListe: {option: ""}, 
      classesListe: {option: ""},
      niveauListe: {option: ""},
      recherche: ""
    };
  },
  computed: {
  },
  methods: {
    initData() {
      this.spellData = this.data
    }, 
    filterSearchBar() {
      this.spellData = this.spellData.filter(spell => spell[1].toLowerCase().includes(this.recherche.toLowerCase()))
    },
    spellSearch() {
      this.initData();
      this.verifyIfOptionSelected();
      this.filterSearchBar();
    },
    optionSelected(listeName) {
      this.initData();
      this.filterSearchBar();

      switch(listeName.name) {
        case "ecole":
          this.ecoleListe = listeName;
          this.spellData = this.spellData.filter(spell => spell[2] === listeName.option);
          break;
        case "branche":
          this.brancheListe = listeName;
          break;
        case "classes":
          this.classesListe = listeName;
          break;
        case "niveau":
          this.niveauListe = listeName;
          break;
      }
    },
    verifyIfOptionSelected() {
      if(this.ecoleListe.option !== "") {
        this.optionSelected(this.ecoleListe);
      }
      if(this.brancheListe.option !== "") {
        this.optionSelected(this.brancheListe);
      }
      if(this.classesListe.option !== "") {
        this.optionSelected(this.classesListe);
      }
      if(this.niveauListe.option !== "") {
        this.optionSelected(this.niveauListe);
      }
    }
  },
};

</script>

<style>
.spellTab:hover {
  color: white;
  background-color: #791cf8;
}
</style>
