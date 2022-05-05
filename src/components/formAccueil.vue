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
<formTable :spellAfficher="spellData" :key="spellData" />
</template>


<script>
import formTable from "./formTable.vue";

export default {
  name: "ongletAccueil",
  props: ["data"],
  components: {
    formTable,
  },
  data: function () {
    return {
      spellData: this.data
    };
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