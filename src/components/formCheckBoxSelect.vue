<template>
  <tr>
    <td>
        <SelectList
          label="Ecole :"
          :options="optionsEcole"
          name="ecole"
          @eventSelectOption="optionSelectFunction"
        />
    </td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchSchoolBox"
        
      />
    </td>
  </tr>
  <tr>
    <td>
        <SelectList
          label="Branche :"
          options="test"
        />
    </td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchBrancheBox"
      />
    </td>
  </tr>
  <tr>
    <td>
        <SelectList
          label="Classes :"
          options="test"
        />
    </td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchClasseBox"
      />
    </td>
  </tr>
  <tr>
    <td>
        <SelectList
          label="Niveau :"
          options="test"
        />
    </td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchLevelBox"
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
    };
  },
  methods: {
    getOccurenceElement(key) { 
      let tousLesElements = data.map(table => table[key]); 
      let tableauElementsUnique = [...new Set(tousLesElements)]; 
      return tableauElementsUnique; 
    },
    getSchools() {
      let tab = []
      tab.push(" ")

      tab = tab.concat(this.getOccurenceElement(2))
      return tab
    },
    optionSelectFunction(name, option) {
      this.$emit('eventOptionSelected', {name, option})
    },
    initSchools() {
      console.log("InitSchools");
      let schools = JSON.parse(localStorage.getItem("ecoles"));
      console.log(schools);
      if (!schools) {
        console.log("schools22");
        schools = this.getSchools();
        localStorage.setItem("ecoles", JSON.stringify(schools));
      }
      return schools;
    },
  },
};
</script>