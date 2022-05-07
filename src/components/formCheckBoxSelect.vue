<template>
  <tr>
    <td>
      <SelectList
        label="Ecole :"
        :options="optionsEcole"
        name="ecole"
        :affiche="config.ecole"
        @eventSelectOption="optionSelectFunction"
      />
    </td>
  </tr>
  <tr>
    <td>
      <SelectList
        label="Branche :"
        :options="optionsBranche"
        name="branche"
        :affiche="config.branche"
        @eventSelectOption="optionSelectFunction"
      />
    </td>
  </tr>
  <tr>
    <td>
      <SelectList
        label="Classes :"
        :options="optionsClasse"
        name="classes"
        :affiche="config.classes"
        @eventSelectOption="optionSelectFunction"
      />
    </td>
  </tr>
  <tr>
    <td>
      <SelectList
        label="Niveau :"
        :options="optionsNiveau"
        name="niveau"
        :affiche="config.niveau"
        @eventSelectOption="optionSelectFunction"
      />
    </td>
  </tr>
</template>

<script>
import SelectList from "./formSelect.vue";
import data from "./../assets/data.min.js"; // Lien vers toutes les données

export default {
  name: "checkBoxSelect",
  components: {
    SelectList,
  },
  emits: ["eventOptionSelected"],
  data: function () {
    return {
      optionsEcole: this.getSchools(),
      optionsBranche: this.getBranches(),
      optionsClasse: this.getClasses(),
      optionsNiveau: this.getLevels(),
      config: this.initConfig()
    };
  },
  methods: {
    getOccurenceElement(key) {
      let tousLesElements = data.map((table) => table[key]);
      let tableauElementsUnique = [...new Set(tousLesElements)];
      return tableauElementsUnique;
    },
    getSchools() {
      let tab = [];
      tab.push(" ");

      tab = tab.concat(this.getOccurenceElement(2));
      return tab;
    },
    getBranches() {
      let tousLesElements = data.map((table) => table[3]);

      let tab = [];
      tab.push(" ");
      tousLesElements.forEach((elem) => {
        tab = tab.concat(elem);
      });
      return [...new Set(tab)];
    },
    getClasses() {
      let tousLesElements = data.map((table) => table[4]);

      let tab = [];
      tab.push(" ");
      tousLesElements.forEach((elem) => {
        elem.forEach((classe) => {
          tab = tab.concat(classe[0]);
        });
      });
      return [...new Set(tab)];
    },
    getLevels() {
      let tousLesElements = data.map((table) => table[4]);

      let tab = [];
      tab.push(" ");
      tousLesElements.forEach((elem) => {
        elem.forEach((level) => {
          tab = tab.concat(level[1]);
        });
      });
      tab.sort();
      return [...new Set(tab)];
    },
    optionSelectFunction(name, option) {
      this.$emit("eventOptionSelected", { name, option });
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