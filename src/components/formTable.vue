<template>
<table>
    <tr>
      <th>Livre</th>
      <th>Nom</th>
      <th>Ecole</th>
      <th>Branche</th>
      <th>Classe</th>
    </tr>
    <!-- On boucle des lignes de tableau
          Chaque entité de spellSearch va être stocké dans spellFor
          Puis on met une clé pour dire sur quoi on boucle, ici le nom, mais c'est inutile dans notre cas
    -->
    <tr v-for="spellFor in spellSearch" :key="spellFor[1]">
      <!--On appel l'élément spell de spellView et on lui donne la valeur de spellFor pour qu'il travaille avec -->
      <spellView :spell="spellFor" />
    </tr>
  </table>

</template>

<script>
import spellView from "./formSpellView.vue";


export default {
  name: "spellTable",
  props: ["spellSearch"],
  components: {
    spellView,
  },
};
</script>
