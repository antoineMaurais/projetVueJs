<template>
  <td>
    <input
      type="text"
      v-model="searchName"
      @input="$emit('spellSearch', this.searchName, this.searchNameBox)"
      placeholder="Rechercher"
    />
  </td>

  <td>Ecoles</td>
  <td>Branches</td>
  <td>Classes</td>
  <td>Niveau</td>
  <td>Livres Disponible</td>
  <td>Livres ajoutés</td>

  <td>
    <input
      type="checkbox"
      v-model="searchNameBox"
      @input="$emit('spellSearch', this.searchName, this.searchNameBox)"
    />
  </td>
  <button>Rechercher</button>
</template>


<script>
export default {
  name: "checkBoxSelect",
  data: function () {
    return { searchName: "", searchNameBox: false };
  },
};
</script>