<template>
  <td v-on:click="afficherDetail(spell[0])">{{ spell[0] }}</td>
  <td>{{ spell[1] }}</td>
  <td>{{ spell[2] }}</td>
  <td>{{ spell[3].join(", ") }}</td>
  <!-- Supprime l'affiche des crochets -->
  <td>{{ spell[4].join(", ") }}</td>
  <!--
  <td>{{ spell[5] }}</td>
  <td>{{ spell[6] }}</td>
  <td>{{ spell[7] }}</td>
  <td>{{ spell[8] }}</td>
  <td>{{ spell[9] }}</td>
  <td>{{ spell[10] }}</td>
  <td>{{ spell[11] }}</td>
  <td>{{ spell[12] }}</td>
  -->
</template>


<script>
export default {
  name: "spellView",
  props: ["spell"],
  methods: {
    afficherButton(spell) {
      console.log(spell);
    },
  },
};
</script>