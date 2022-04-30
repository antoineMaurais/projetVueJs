<template>
  <checkBoxSelect @Search="updateSearch" />
  <!--<h3>Nombre total de sorts trouvés: {{ spellSearch.length }}</h3>-->
  <spellTable :spellAfficher="spellSearch" />
</template>

<script>
import spellTable from "./formTable.vue";
//import checkBoxSearchName from "./formCheckBoxSearchName.vue";
import checkBoxSelect from "./formCheckBoxSelect.vue";

export default {
  name: "ongletRecherche",
  props: ["spellData"],
  components: {
    spellTable,
    checkBoxSelect,
  },
  data: function () {
    return {
      searchName: "",
      searchNameBox: "",
    };
  },
  cumputed: {
    spellSearch() {
      console.log("test");
      console.log(this.searchNameBox);
      console.log(this.searchName);
      console.log(this.spellData);

      if (this.searchNameBox)
        return this.spellData.filter((spell) =>
          spell[1].toLowerCase().includes(this.searchName.toLowerCase())
        );
      else return [];
    },
  },
  methods: {
    updateSearch(searchName, searchNameBox) {
      this.searchName = searchName;
      this.searchNameBox = searchNameBox;
    },
  },
};
</script>

<style>
.spellTab:hover {
  color: white;
  background-color: #791cf8;
}
</style>
